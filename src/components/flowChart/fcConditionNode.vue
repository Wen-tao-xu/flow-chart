<!--
 * @Author: xwt
 * @Date: 2020-09-27 16:20:32
 * @LastEditors: xwt
 * @LastEditTime: 2020-09-30 16:17:14
 * @Description: Do not edit
 * @FilePath: \flow-chart\src\components\flowChart\fcConditionNode.vue
-->
<template>
  <div class="condition-node fc-row">
    <div class="top-left-cover-line" v-if="isRowBeginNode"></div>
    <div class="top-right-cover-line" v-if="isRowEndNode"></div>
    <div class="condition-node-box">
      <div class="line"></div>
      <div class="node-content">分支节点</div>
      <fcAddBar @onHandleMenu="onHandleMenu" />
    </div>
    <div class="fc-row" v-if="data.children && data.children.length">
      <component
        :is="getComponent(item.type)"
        v-for="(item, i) in data.children"
        :key="i"
        :data="item"
        :index="i"
        :parentData="data.children"
      ></component>
    </div>
    <div class="bottom-left-cover-line" v-if="isRowBeginNode"></div>
    <div class="bottom-right-cover-line" v-if="isRowEndNode"></div>
  </div>
</template>

<script>
import fcAddBar from './fcAddBar'
import { getComponent } from './utils'
export default {
  name: 'fcConditionNode',
  components: {
    fcAddBar,
    fcDealNode: () => import('./fcDealNode'),
    fcBranch: () => import('./fcBranch'),
  },
  props: {
    isRowBeginNode: {
      type: Boolean,
      default: false,
      required: true,
    },
    isRowEndNode: {
      type: Boolean,
      default: false,
      required: true,
    },
    data: {
      type: Object,
      default: () => {},
      required: true,
    },
  },
  methods: {
    onHandleMenu(type) {
      let obj = { type }
      if (type === 'condition') {
        obj.children = [{type}, {type}]
      }
      if(!this.data.children) {
        this.$set(this.data, 'children', [])
      }
      this.data.children.unshift(obj)
    },
    getComponent(type) {
      return getComponent(type)
    },
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