<template>
  <div>
    <h1>
      Political Indicators
    </h1>
  </div>

  <div class="container">
    <div class="row align-items-start">
      <div class="col">
        <OrdersChart /><br />
        <InitialApprovalChart /><br />
        <FinalApprovalChart /><br/>
      </div>
    </div>
  </div>
</template>

<script setup>
import OrdersChart from '../components/OrdersChart.vue'
import InitialApprovalChart from '../components/InitialApprovalChart.vue'
import FinalApprovalChart from '../components/FinalApprovalChart.vue'
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