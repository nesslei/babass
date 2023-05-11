<script setup>
import { RouterView } from 'vue-router'
import ChartPie from './components/ChartPie.vue'

</script>

<template>
  <h2> i POOPED my pants</h2>
  <RouterView></RouterView>
  <ChartPie></ChartPie>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

</style>
