<template>
  <div id="app">
    <Header :symbol="products"/>
    <FormatSelector v-on:choiceFormat="sendData($event,false)"/>
    <AddProduct v-on:entry="sendData($event,true)"/>
    <Price :result="price"/>
    <Basket :resultBasket="basket"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import FormatSelector from './components/FormatSelector.vue'
import AddProduct from './components/AddProducts.vue'
import Price from './components/Price.vue'
import Basket from './components/Basket.vue'

export default {
  name: 'App',
  data () {
    return {
      products: "",
      price: "",
      basket: ""
    }
  },
  components: {
    Header,
    AddProduct,
    Price,
    Basket,
    FormatSelector
  },
  methods: {
    findData: function() {
      this.$axios.get("http://localhost:7373/").then(response => (this.formatData(response.data)))
    },
    formatData: function(data) {
      this.products = this.formatSymbol(data.symbol)
      this.price = data.results
      this.basket = this.formatSymbol(data.basket)
    },
    formatSymbol: function(arr) {
      let result = "";
      for (let i = 0; i < arr.length; i++) {
        result += arr[i] + " "
      }
      return result;
    },
    sendData: function(arg, isAddProducts) {
      let routes = "";
      if (isAddProducts) {
        routes = "add";
      } else {
        routes = "select";
      }
      this.$axios.post("http://localhost:7373/" + routes, JSON.stringify({arg}))
      this.findData()
    }
  },
  mounted() {
    this.findData()
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  
}

body {
  color: #fff;
  background-color: #2f3136;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  min-height: 100vh;
}
</style>
