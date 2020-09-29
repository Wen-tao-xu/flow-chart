<!--
 * @Author: xwt
 * @Date: 2020-09-27 10:24:24
 * @LastEditors: xwt
 * @LastEditTime: 2020-09-29 15:41:59
 * @Description: Do not edit
 * @FilePath: \flow-chart\src\components\flowChart\index.vue
-->
<template>
  <div class="fc-wrapper">
    <div class="fc-container">
      <fcItem v-for="(item, index) in flowChart" :key="index" :data="item" />
      <div class="end-node">结束</div>
    </div>
  </div>
</template>

<script>
import fcItem from './fcItem'
export default {
  name: 'flowChart',
  components: {
    fcItem,
  },
  data() {
    return {
      flowChart: [
        {
          type: 'dealNode'
        }
      ],
    }
  },
  methods: {
    getComponent(type) {
      switch (type) {
        case 'condition':
          return 'fcBranch'
        case 'dealNode':
          return 'fcDealNode'
      }
    },
  },
}
</script>

<style scoped>
@import url('./style/index.css');
.fc-wrapper, .fc-container {
  display: flex;
  height: 100%;
  width: 100%;
  box-sizing: border-box;
}
.fc-container {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #f5f5f7;
  padding: 50px 20px;
  /* transform: scale(0.5); */
}
.end-node {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  width: 50px;
  height: 50px;
  background: linear-gradient(-120deg, #dfdfe8 1%, #afafb8);
  box-shadow: 0 1px 5px 0 rgba(0, 0, 0, 0.2);
  border-radius: 100%;
  color: #fff;
}
</style>