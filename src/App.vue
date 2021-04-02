<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <p>{{ info }}</p>
    <AddProduct />
  </div>
</template>

<script>
import AddProduct from './components/AddProducts.vue'

export default {
  name: 'App',
  data () {
    return {
      info: ""
    }
  },
  components: {
    AddProduct
  },

  mounted () {
    this.$axios.get("http://localhost:7373/").then(response => (this.info = response.data.products))
  },
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
