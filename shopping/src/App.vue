<template>
  <ShoppingProdutos msg="Shopping"/>
</template>

<script>
import ShoppingProdutos from './components/ShoppingProdutos.vue';

export default {
  name: 'App',
  components: {
    ShoppingProdutos
}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>