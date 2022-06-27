<template>
  <div id="app">
    <my-header></my-header>
    <my-footer></my-footer>
  </div>
</template>

<script>
import MyFooter from './components/MyFooter.vue'
import MyHeader from './components/MyHeader.vue'
export default {
  components: { MyFooter, MyHeader }
}
</script>

<style></style>
