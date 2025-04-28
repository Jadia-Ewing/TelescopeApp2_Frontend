<template>
  <div class="p-4 border rounded shadow bg-white">
    <h2 class="text-lg font-bold">Humidity Chart (Last Hour)</h2>
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
  name: 'HumidityChart',
  components: { Line },
  data() {
    return {
      chartData: {
        labels: Array.from({ length: 12 }, (_, i) => `${i * 5}m ago`),
        datasets: [{
          label: 'Humidity (%)',
          data: [70, 72, 75, 77, 76, 80, 85, 82, 78, 76, 74, 73],
          borderColor: 'blue',
          backgroundColor: 'lightblue',
          fill: true,
          tension: 0.4
        }]
      },
      chartOptions: {
        responsive: true,
        plugins: { legend: { position: 'top' } },
        scales: { y: { min: 60, max: 100 } }
      }
    }
  }
}
</script>
