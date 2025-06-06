<template>
  <div id="app">
    <PerformanceChartEcharts />
  </div>
</template>

<script>
import PerformanceChartEcharts from './components/PerformanceChartEcharts.vue'

export default {
  name: 'App',
  components: {
    PerformanceChartEcharts
  }
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>