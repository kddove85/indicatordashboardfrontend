<template>
  <div>
    <h1>
      Climate Indicators
    </h1>
  </div>

  <div class="container">
    <div class="row align-items-start">
      <div class="col">
        <TemperatureChart /><br />
      </div>
    </div>
  </div>
</template>

<script setup>
import TemperatureChart  from '../components/TemperatureChart.vue'
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
