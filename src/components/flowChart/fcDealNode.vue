<!--
 * @Author: xwt
 * @Date: 2020-09-27 11:34:12
 * @LastEditors: xwt
 * @LastEditTime: 2020-09-29 14:17:13
 * @Description: Do not edit
 * @FilePath: \flow-chart\src\components\flowChart\fcDealNode.vue
-->
<template>
  <div class="deal-node-wrap">
    <div class="deal-node">
      <div class="node-content audit-background">
        <p>普通节点</p>
        <i class="del-btn">X</i>
      </div>
      <div class="line-in-middle">
        <div class="line"></div>
        <fcAddBar />
      </div>
    </div>
    <div class="fc-row" v-if="data && data.children && data.children.length">
      <fcItem
        v-for="(item, index) in data.children"
        :key="index"
        :data="item"
      />
    </div>
  </div>
</template>

<script>
import fcAddBar from './fcAddBar'
import fcItem from './fcItem'
export default {
  name: 'fcDealnode',
  components: {
    fcAddBar,
    fcItem,
    // fcBranch: () => import('./fcBranch'),
  },
  props: {
    data: {
      type: Object,
      default: () => {},
    },
  },
  computed: {
    children() {
      return this.data.children || []
    },
  },
  data() {
    return {}
  },
  methods: {
    getComponent(type) {
      switch (type) {
        case 'condition':
          return 'fcBranch'
        case 'dealNode':
          return 'fc-dealnode'
      }
    },
  }
}
</script>

<style scoped>
.deal-node-wrap {
  display: flex;
  align-items: center;
  flex-direction: column;
}
</style>