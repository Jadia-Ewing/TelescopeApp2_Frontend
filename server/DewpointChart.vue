<template>
    <div class="p-4 border rounded shadow bg-white">
      <h2 class="text-lg font-bold">Dew Point Over Time</h2>
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
    name: 'DewpointChart',
    components: { Line },
    data() {
      return {
        chartData: {
          labels: Array.from({ length: 12 }, (_, i) => `${i * 5}m ago`),
          datasets: [{
            label: 'Dew Point (°F)',
            data: [60, 61, 62, 63, 62, 62, 63, 64, 65, 64, 63, 62],
            borderColor: 'green',
            backgroundColor: 'lightgreen',
            tension: 0.4
          }]
        },
        chartOptions: {
          responsive: true,
          plugins: { legend: { position: 'top' } },
          scales: { y: { min: 55, max: 70 } }
        }
      }
    }
  }
  </script>
  