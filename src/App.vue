<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <p>{{ info }}</p>
    <AddProduct v-on:entry="sendData($event)"/>
  </div>
</template>

<script>
import AddProduct from './components/AddProducts.vue'

export default {
  name: 'App',
  data () {
    return {
      info: "",
    }
  },
  components: {
    AddProduct
  },
  methods: {
    findData: function() {
      this.$axios.get("http://localhost:7373/").then(response => (this.info = response.data))
    },
    sendData: function(arg) {
      this.$axios.post("http://localhost:7373/add", JSON.stringify({arg}))
      this.findData()
    }
  },
  mounted() {
    this.findData()
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
