<template>
  <div>
    <NuxtLink to="/todo">TODOリスト</NuxtLink>
    <h1>vue-chartjsで棒グラフ</h1>
    <BarChart />
  </div>
</template>

<script>
import BarChart from '../components/BarChart.vue'

export default {
  components: {
    BarChart
  }
}
</script>