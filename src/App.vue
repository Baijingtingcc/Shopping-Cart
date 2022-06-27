<template>
  <div id="app">
    <my-header title="购物车" background="pink" color="black"></my-header>
    <component :is="componentName"></component>
    <my-footer @changeCon="componentName = $event"></my-footer>
  </div>
</template>

<script>
import MyFooter from './components/MyFooter.vue'
import MyHeader from './components/MyHeader.vue'
import MyGoodsList from './views/MyGoodsList.vue'
import MyGoodsSearch from './views/MyGoodsSearch.vue'
import MyUserInfo from './views/MyUserInfo.vue'
export default {
  components: { MyFooter, MyHeader, MyGoodsList, MyGoodsSearch, MyUserInfo },
  data() {
    return {
      componentName: MyGoodsList
    }
  }
}
</script>

<style scoped>
#app {
  margin: 50px 0;
}
</style>
