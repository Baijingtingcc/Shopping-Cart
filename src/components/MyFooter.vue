<template>
  <div class="my-tab-bar">
    <div
      :class="['tab-item', { current: currIndex === index }]"
      v-for="(item, index) in tabList"
      :key="index"
      @click="currName(index, item.componentName)"
    >
      <!-- 图标 -->
      <span :class="`iconfont ${item.iconText}`"></span>
      <!-- 文字 -->
      <span style="margin-top: -10px">{{ item.text }}</span>
    </div>
  </div>
</template>

<script>
import '@/assets/fonts/iconfont.css'
export default {
  data() {
    return {
      tabList: [
        {
          iconText: 'icon-shangpinliebiao',
          text: '商品列表',
          componentName: 'MyGoodsList'
        },
        {
          iconText: 'icon-sousuo',
          text: '商品搜索',
          componentName: 'MyGoodsSearch'
        },
        {
          iconText: 'icon-user',
          text: '我的信息',
          componentName: 'MyUserInfo'
        }
      ],
      currIndex: 0
    }
  },
  methods: {
    currName(index, tagname) {
      this.currIndex = index
      this.$emit('changeCon', tagname)
    }
  }
}
</script>

<style lang="less" scoped>
.my-tab-bar {
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
  height: 50px;
  border-top: 1px solid #ccc;
  display: flex;
  justify-content: space-around;
  align-items: center;
  background-color: white;
  .tab-item {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
}

.current {
  color: #1d7bff;
  .iconfont {
    color: pink;
  }
}
</style>
