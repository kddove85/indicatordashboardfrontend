<template>
  <div>
    <h1>
      Indicators Home Page
    </h1>
  </div>

  <div class="container">
    <div class="row align-items-start">
      <div class="col">
        <EarningsTable />
      </div>
    </div>
  </div>
</template>

<script setup>
  import EarningsTable from '../components/EarningsTable.vue'
</script>