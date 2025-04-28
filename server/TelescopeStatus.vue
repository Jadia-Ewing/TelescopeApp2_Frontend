<template>
  <div class="p-4 border rounded shadow-md">
    <h2>Telescope Status Evaluation</h2>
    <p v-if="isUsable"> Telescope is usable.</p>
    <p v-else> Telescope is not usable.</p>
  </div>
</template>

<script>
export default {
  props: ['weatherData'],
  computed: {
    isUsable() {
      const { windSpeed, humidity, rainChance, cloudCoverage } = this.weatherData;
      return windSpeed < 30 && humidity < 90 && rainChance < 50 && cloudCoverage < 80;
    }
  }
}
</script>

