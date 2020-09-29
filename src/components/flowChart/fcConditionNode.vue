<!--
 * @Author: xwt
 * @Date: 2020-09-27 16:20:32
 * @LastEditors: xwt
 * @LastEditTime: 2020-09-29 14:28:51
 * @Description: Do not edit
 * @FilePath: \flow-chart\src\components\flowChart\fcConditionNode.vue
-->
<template>
  <div class="fc-row">
    <!-- {{data}} -->
    <div class="condition-node fc-row">
      <div class="top-left-cover-line" v-if="isRowBeginNode"></div>
      <div class="top-right-cover-line" v-if="isRowEndNode"></div>
      <div class="condition-node-box">
        <div class="line"></div>
        <div class="node-content">分支节点</div>
        <fcAddBar />
      </div>
      <div class="bottom-left-cover-line" v-if="isRowBeginNode"></div>
      <div class="bottom-right-cover-line" v-if="isRowEndNode"></div>
    </div>
    <fcItem :data="data" />
  </div>
</template>

<script>
import fcAddBar from './fcAddBar'
import fcItem from './fcItem'
export default {
  name: 'fcConditionNode',
  components: {
    fcAddBar,
    fcItem,
    // fcDealNode: () => import ('./fcDealNode'),
    // fcBranch: () => import('./fcBranch')
  },
  props: {
    isRowBeginNode: {
      type: Boolean,
      default: false,
    },
    isRowEndNode: {
      type: Boolean,
      default: false,
    },
    data: {
      type: Object,
      default: () => {},
    },
  },
  computed: {
    children() {
      return this.data.children || []
    }
  },
  data() {
    return {}
  },
}
</script>

<style scoped>
.condition-node-box {
  padding: 30px 50px 0;
  position: relative;
  flex-grow: 1;
}
</style>