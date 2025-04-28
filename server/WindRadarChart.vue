<template>
    <div class="p-4 border rounded shadow bg-white relative">
      <h2 class="text-lg font-bold mb-2">Wind Speed & Direction (Radar)</h2>
  
      <!-- Wind Direction Compass -->
      <div class="absolute top-2 right-4 text-center text-sm font-semibold">
        <div class="w-20 h-20 rounded-full border-2 border-blue-600 flex items-center justify-center relative">
          <div
            class="w-1 h-8 bg-red-600 absolute origin-bottom"
            :style="`transform: rotate(${dummyDirection}deg);`"
          ></div>
          <span class="absolute bottom-0 text-blue-600 font-bold">N</span>
        </div>
        <div class="mt-1 text-gray-600">Dir: {{ dummyDirection }}°</div>
      </div>
  
      <!-- Radar Chart -->
      <PolarArea :data="chartData" :options="chartOptions" />
    </div>
  </template>
  
  <script>
  import { PolarArea } from 'vue-chartjs'
  import {
    Chart as ChartJS,
    Title, Tooltip, Legend,
    RadialLinearScale, ArcElement
  } from 'chart.js'
  
  ChartJS.register(
    Title, Tooltip, Legend,
    RadialLinearScale, ArcElement
  )
  
  export default {
    name: 'WindRadarChart',
    components: { PolarArea },
    data() {
      return {
        dummyDirection: 135,
        chartData: {
          labels: ['N', 'NE', 'E', 'SE', 'S', 'SW', 'W', 'NW'],
          datasets: [
            {
              label: 'Sustained Wind (mph)',
              data: [5, 8, 4, 11, 7, 3, 6, 9],
              backgroundColor: 'rgba(54, 162, 235, 0.5)',
              borderColor: 'rgba(54, 162, 235, 1)',
              borderWidth: 1
            },
            {
              label: 'Wind Gusts (mph)',
              data: [9, 12, 7, 16, 10, 6, 10, 13],
              backgroundColor: 'rgba(255, 99, 132, 0.4)',
              borderColor: 'rgba(255, 99, 132, 1)',
              borderWidth: 1
            }
          ]
        },
        chartOptions: {
          responsive: true,
          plugins: {
            legend: { position: 'bottom' }
          },
          scales: {
            r: {
              beginAtZero: true,
              max: 20,
              ticks: {
                stepSize: 5
              }
            }
          }
        }
      }
    }
  }
  </script>
  
  <style scoped>
  [style*="transform: rotate"] {
    transition: transform 1s ease;
  }
  </style>
  