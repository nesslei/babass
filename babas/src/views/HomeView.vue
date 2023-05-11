<script setup>
import ChartPie from '../components/ChartPie.vue'
import { RouterView } from 'vue-router'
import { ref, onMounted } from 'vue'

const child = ref('')
async function getChild() {
  let res = await fetch('https://data.cityofnewyork.us/resource/fcau-jc6k.json?year=2007')
  let data = await res.json()
  child.value = data.results
}

onMounted(() => {
  getChild()
})
</script>

<template>
  <div>
    <h2> i POOPED my pants</h2>
    <RouterView></RouterView>
    <ChartPie></ChartPie>
  </div>
</template>

<style scoped>

</style>