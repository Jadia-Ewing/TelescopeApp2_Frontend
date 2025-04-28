<template>
  <div class="min-h-screen bg-gradient-to-b from-blue-100 to-blue-300 font-sans">
    <!-- Header -->
    <header class="text-center py-6 bg-blue-700 text-white">
      <h1 class="text-4xl font-bold">Weather Radar for the ERAU 1-Meter Telescope</h1>
      <p class="text-lg mt-2">Developed by Team Frontend - Alvin, Jadia, Joe, Christian</p>
    </header>

    <!-- Main Grid Layout -->
    <main class="grid grid-cols-3 gap-6 px-8 py-6">
      <!-- Left Column -->
      <section class="space-y-4">
        <WindRadarChart />

        <div class="p-4 border rounded shadow bg-white">
          <h2 class="font-bold text-lg">Telescope Camera</h2>
          <div class="h-40 flex items-center justify-center text-gray-500">[ Camera Feed Placeholder ]</div>
        </div>

        <div class="p-4 border rounded shadow bg-white">
          <h2 class="font-bold text-lg">Student Recordings</h2>
          <div class="h-32 flex items-center justify-center text-gray-500">[ Upload Feature Placeholder ]</div>
        </div>
      </section>

      <!-- Middle Column -->
      <section class="space-y-4">
        <HumidityChart />
        <TemperatureChart />
        <DewpointChart />
      </section>

      <!-- Right Column -->
      <section class="space-y-4">
        <AlertStatus :alertType="dummyAlertType" />

        <div class="p-4 border rounded shadow bg-white">
          <h2 class="font-bold text-lg">Sensor Status</h2>
          <p class="text-gray-700">All systems operational</p>
        </div>

        <WeatherDisplay :weatherData="dummyWeather" />
        <TelescopeStatus :weatherData="dummyWeather" />
      </section>
    </main>
  </div>
</template>

<script>
import WeatherDisplay from './components/WeatherDisplay.vue'
import HumidityChart from './components/HumidityChart.vue'
import TelescopeStatus from './components/TelescopeStatus.vue'
import AlertStatus from './components/AlertStatus.vue'
import WindRadarChart from './components/WindRadarChart.vue'
import TemperatureChart from './components/TemperatureChart.vue'
import DewpointChart from './components/DewpointChart.vue'

export default {
  name: 'App',
  components: {
    WeatherDisplay,
    HumidityChart,
    TelescopeStatus,
    AlertStatus,
    WindRadarChart,
    TemperatureChart,
    DewpointChart
  },
  data() {
    return {
      dummyWeather: {
        windSpeed: 12,
        windDirection: 135,
        humidity: 76,
        rainChance: 35,
        cloudCoverage: 45,
        temperature: 75,
        dewpoint: 65
      },
      dummyAlertType: 'Caution'
    }
  }
}
</script>

<style>
body {
  margin: 0;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
</style>
