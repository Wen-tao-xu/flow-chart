<!--
 * @Author: xwt
 * @Date: 2020-09-29 10:23:12
 * @LastEditors: xwt
 * @LastEditTime: 2020-09-29 10:48:38
 * @Description: Do not edit
 * @FilePath: \flow-chart\src\components\flowChart\fcItem.vue
-->
<template>
  <component :is="getComponent(data.type)" :data="data"></component>
</template>

<script>
export default {
  name: 'fcItem',
  components: {
    fcDealNode: () => import('./fcDealNode'),
    fcBranch: () => import('./fcBranch'),
  },
  props: {
    data: {
      type: Object,
      default: () => {},
    },
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

<style>
</style>