<template>
  <div
    id="app"
    class="container mx-auto p-4"
  >
    <!-- Existing code here -->

    <div v-if="imageData">
      <img
        :src="imageData"
        alt=""
      />
    </div>
    <div
      class="row"
      v-else
    >
      <div class="col-sm w-full">
        <video
          ref="video"
          autoplay
          class="w-full"
          style="max-width: 100%"
        ></video>
        <!-- Add button to capture image -->
        <button
          class="btn btn-primary w-full bg-blue-500 text-white py-2 px-4 rounded mb-2"
          :disabled="active"
          type="button"
          @click="captureImage"
        >
          Capture Image
        </button>
      </div>
    </div>
    <!-- Existing code here -->
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const video = ref<HTMLVideoElement | null>(null)
const imageData = ref<string | null>(null) // imageData should be a ref<string | null>

const initCamera = async () => {
  try {
    const stream = await navigator.mediaDevices.getUserMedia({ video: true })
    if (video.value) {
      video.value.srcObject = stream
    }
  } catch (error) {
    console.error('Error accessing camera:', error)
    // Handle error here
  }
}

const captureImage = () => {
  const canvas = document.createElement('canvas')
  if (video.value) {
    canvas.width = video.value.videoWidth
    canvas.height = video.value.videoHeight
    canvas.getContext('2d')?.drawImage(video.value, 0, 0, canvas.width, canvas.height)
    imageData.value = canvas.toDataURL('image/png') // Set imageData.value instead of directly assigning

    // Now you can do something with the captured image data
    console.log('Captured image data:', imageData.value)
  }
}

onMounted(() => {
  initCamera()
})

onUnmounted(() => {
  if (video.value && video.value.srcObject) {
    const tracks = video.value.srcObject.getTracks()
    tracks.forEach(track => track.stop())
  }
})
</script>
