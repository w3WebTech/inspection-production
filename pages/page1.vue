<template>
  <div
    id="app"
    class="container mx-auto p-4"
  >
    <div class="py-2 text-bold">Latitude</div>
    <div class="py-2 px-4">{{ location && location.latitude }}</div>
    <div class="py-2 text-bold">Longitude</div>
    <div class="py-2 px-4">{{ location && location.longitude }}</div>
    <!-- Rest of your template code -->
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, reactive } from 'vue'
import axios from 'axios'
import moment from 'moment'

// Reactive state
const state = reactive({
  id: null as number | null,
  active: false,
  server: 'https://app.yetcargo.melisa.mx:8044/',
  endpoint: '/locations',
  watchOperationId: null as NodeJS.Timeout | null,
  frequency: 2000,
  autoUpdate: true,
  color: 'blue',
  visibilityState: true,
  error: '',
  errorSendLocation: '',
  locations: [] as Array<any>,
})

// Location object
const location = reactive({
  latitude: 0,
  longitude: 0,
  accuracy: 0,
  speed: 0,
  timestamp: 0,
})

// Axios instance
const axiosInstance = axios.create({
  baseURL: state.server,
  timeout: 10000,
})

// Methods
const handleVisibilityChange = () => {
  if (document.visibilityState === 'hidden') {
    state.visibilityState = false
    stop()
  } else {
    state.visibilityState = true
    init()
  }
}

const getHumanTime = (timestamp: number) => {
  return moment(timestamp).format('YYYY-MM-DD HH:mm:ss')
}

const sendLocation = (location: any) => {
  axiosInstance
    .post(state.endpoint, location)
    .then(response => {
      console.log(response)
      state.errorSendLocation = ''
    })
    .catch(err => {
      console.error(err)
      state.errorSendLocation = err.message
    })
}

const init = () => {
  state.active = true
  updateLocation()
}

const stop = () => {
  if (state.watchOperationId) {
    clearInterval(state.watchOperationId)
    state.watchOperationId = null
  }
  state.active = false
}

const fireUpdate = (position: GeolocationPosition) => {
  const newLocation = {
    longitude: position.coords.longitude,
    latitude: position.coords.latitude,
    accuracy: position.coords.accuracy,
    speed: position.coords.speed,
    timestamp: position.timestamp,
    color: state.color,
    id: state.id,
  }
  console.log('GPS location', position)

  if (location.latitude === newLocation.latitude && location.longitude === newLocation.longitude) {
    console.log('Equal location, ignore')
  } else {
    Object.assign(location, newLocation)
    state.locations.push(newLocation)
    sendLocation(newLocation)
  }
}

const fireError = (error: GeolocationPositionError) => {
  console.error(error)
  state.error = error.message
}

const updateLocation = () => {
  if (state.watchOperationId) {
    clearInterval(state.watchOperationId)
  }

  if (!state.autoUpdate) {
    return
  }

  state.watchOperationId = setInterval(() => {
    navigator.geolocation.getCurrentPosition(fireUpdate, fireError, {
      maximumAge: 0,
      timeout: Infinity,
      enableHighAccuracy: true,
    })
  }, state.frequency)
}

onMounted(() => {
  document.addEventListener('visibilitychange', handleVisibilityChange, false)
  init()
})
</script>
