<template>
    <div class="p-4 border rounded shadow bg-white">
      <h2 class="text-lg font-bold">Temperature Over Time</h2>
      <Line :data="chartData" :options="chartOptions" />
    </div>
  </template>
  
  <script>
  import { Line } from 'vue-chartjs'
  import {
    Chart as ChartJS,
    Title, Tooltip, Legend,
    LineElement, PointElement,
    CategoryScale, LinearScale
  } from 'chart.js'
  
  ChartJS.register(
    Title, Tooltip, Legend,
    LineElement, PointElement,
    CategoryScale, LinearScale
  )
  
  export default {
    name: 'TemperatureChart',
    components: { Line },
    data() {
      return {
        chartData: {
          labels: Array.from({ length: 12 }, (_, i) => `${i * 5}m ago`),
          datasets: [{
            label: 'Temperature (°F)',
            data: [72, 73, 74, 75, 76, 76, 75, 74, 73, 72, 71, 70],
            borderColor: 'red',
            backgroundColor: 'salmon',
            tension: 0.4
          }]
        },
        chartOptions: {
          responsive: true,
          plugins: { legend: { position: 'top' } },
          scales: { y: { min: 65, max: 80 } }
        }
      }
    }
  }
  </script>
  