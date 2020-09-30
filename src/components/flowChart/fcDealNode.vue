<!--
 * @Author: xwt
 * @Date: 2020-09-27 11:34:12
 * @LastEditors: xwt
 * @LastEditTime: 2020-09-30 16:17:37
 * @Description: Do not edit
 * @FilePath: \flow-chart\src\components\flowChart\fcDealNode.vue
-->
<template>
  <div class="deal-node fc-row">
    <div class="node-content audit-background">
      <p>普通节点</p>
      <i class="del-btn">X</i>
    </div>
    <div class="line-in-middle">
      <div class="line"></div>
      <fcAddBar @onHandleMenu="onHandleMenu" />
    </div>
  </div>
</template>

<script>
import fcAddBar from './fcAddBar'
export default {
  name: 'fcDealnode',
  components: {
    fcAddBar,
  },
  props: {
    data: {
      type: Object,
      default: () => {
        return {}
      },
      required: true
    },
    index: {
      type: Number,
      default: 0,
      required: true
    },
    parentData: {
      type: Array,
      default: () => [],
      required: true
    },
  },
  data() {
    return {}
  },
  methods: {
    onHandleMenu(type) {
      let obj = { type }
      if (type === 'condition') {
        obj.children = [{type}, {type}]
      }
      this.parentData.splice(this.index + 1, 0, obj)
    },
  },
}
</script>

<style scoped>
.deal-node-wrap {
  display: flex;
  align-items: center;
  flex-direction: column;
}
</style>