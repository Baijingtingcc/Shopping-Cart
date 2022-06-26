<template>
  <div class="app">
    <!-- 除了驼峰, 还可以使用-转换链接 -->
    <MyHeader title="购物车" background="pink" color="black" />
    <MyGoods v-for="item in goodsList" :key="item.goods_id" :goods="item" />
    <MyFooter :goodsList="goodsList" />
  </div>
</template>

<script>
// 1.0 样式引入
// 引入组件
import MyHeader from '@/components/MyHeader'
import MyGoods from '@/components/MyGoods'
import MyFooter from '@/components/MyFooter'
import axios from 'axios'
axios.defaults.baseURL = 'https://applet-base-api-t.itheima.net'
axios.defaults.timeout = 3000
export default {
  components: {
    MyHeader,
    MyGoods,
    MyFooter
  },
  data() {
    return {
      // 准备数据
      goodsList: []
    }
  },
  mounted() {
    this.addBooks()
  },
  methods: {
    async addBooks() {
      const res = await axios({ url: '/api/cart' })
      this.goodsList = res.data.list
    }
  }
}
</script>

<style lang="less" scoped>
.app {
  padding: 50px 0;
  max-height: 100vh;
  box-sizing: border-box;
  overflow: auto;
}
</style>
