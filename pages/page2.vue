<script setup lang="ts">
import { onMounted, ref } from 'vue'
import { Chart, registerables } from 'chart.js'

Chart.register(...registerables)

const radarChart = ref<HTMLCanvasElement | null>(null)

const data = {
  labels: [
    'Eating',
    'Drinking',
    'Sleeping',
    'Designing',
    'Coding',
    'Cycling',
    'Running',
  ],
  datasets: [{
    label: 'My First Dataset',
    data: [65, 59, 90, 81, 56, 55, 40],
    fill: true,
    backgroundColor: 'rgba(255, 99, 132, 0.2)',
    borderColor: 'rgb(255, 99, 132)',
    pointBackgroundColor: 'rgb(255, 99, 132)',
    pointBorderColor: '#fff',
    pointHoverBackgroundColor: '#fff',
    pointHoverBorderColor: 'rgb(255, 99, 132)',
  }, {
    label: 'My Second Dataset',
    data: [28, 48, 40, 19, 96, 27, 100],
    fill: true,
    backgroundColor: 'rgba(54, 162, 235, 0.2)',
    borderColor: 'rgb(54, 162, 235)',
    pointBackgroundColor: 'rgb(54, 162, 235)',
    pointBorderColor: '#fff',
    pointHoverBackgroundColor: '#fff',
    pointHoverBorderColor: 'rgb(54, 162, 235)',
  }],
}

const config = {
  type: 'radar',
  data,
  options: {
    elements: {
      line: {
        borderWidth: 3,
      },
    },
  },
}

onMounted(() => {
  if (radarChart.value)
    new Chart(radarChart.value.getContext('2d') as CanvasRenderingContext2D, config)
})
</script>

<template>
  <div>
    <canvas ref="radarChart" />
  </div>
</template>

<style scoped>
canvas {
  width: 100%;
  height: 400px;
}
</style>
