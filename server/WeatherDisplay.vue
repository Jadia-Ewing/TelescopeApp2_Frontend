<template>
  <div class="p-4 border rounded shadow-md">
    <h2>Weather Data</h2>
    <ul>
      <li><strong>Wind Speed:</strong> {{ weatherData.windSpeed }} km/h</li>
      <li><strong>Humidity:</strong> {{ weatherData.humidity }}%</li>
      <li><strong>Rain Chance:</strong> {{ weatherData.rainChance }}%</li>
      <li><strong>Cloud Coverage:</strong> {{ weatherData.cloudCoverage }}%</li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['weatherData']
}
</script>
