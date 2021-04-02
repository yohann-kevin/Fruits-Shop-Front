<template>
  <div id="add-products">
    <input type="text" id="fruit" ref="fruit">
    <button id="scan" v-on:click="sendValue()">Scanner</button>
  </div>
</template>

<script>
export default {
  name: "",
  methods: {
    sendValue: function () {
      this.$emit("entry", this.$refs.fruit.value)
    }
  },
}
</script>

<style scoped>

</style>
