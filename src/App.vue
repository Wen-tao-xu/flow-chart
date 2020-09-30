<!--
 * @Author: xwt
 * @Date: 2020-09-27 10:21:55
 * @LastEditors: xwt
 * @LastEditTime: 2020-09-30 16:00:28
 * @Description: Do not edit
 * @FilePath: \flow-chart\src\App.vue
-->
<template>
  <div id="app">
    <flowChart />
  </div>
</template>

<script>
import flowChart from '@/components/flowChart'
export default {
  name: 'App',
  components: {
    flowChart,
  },
}
</script>

<style>
body,
html {
  margin: 0;
  position: relative;
  height: 100%;
  -webkit-font-smoothing: antialiased;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
  min-height: 100%;
}
</style>
