<template>
  <div class="p-4 border rounded shadow-md">
    <h2 class="font-bold">Alert Status</h2>
    <p :style="{ color: alertColor, fontWeight: 'bold' }">
      Status: {{ alertType }}
    </p>
  </div>
</template>

<script>
export default {
  props: ['alertType'],
  computed: {
    alertColor() {
      switch (this.alertType) {
        case 'Safe':
          return 'green'
        case 'Caution':
          return 'orange'
        case 'Unsafe':
          return 'red'
        default:
          return 'gray'
      }
    }
  }
}
</script>
