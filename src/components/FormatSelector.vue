<template>
  <div>
    <label for="format">Select format (default cents) : </label><br>
    <select name="format" ref="format">
      <option name="default">Select output format</option>
      <option name="euro" value="euro">Euro</option>
      <option name="centime" value="cents">Centime</option>
      <option name="dollars" value="dollars">Dollars</option>
      <option name="yen" value="yen">Yen</option>
      <option name="livre" value="livre">Livre Sterling</option>
      <option name="yuan" value="yuan">Yuan</option>
      <option name="bitcoin" value="bitcoin">Bitcoin</option>
    </select>
    <button type="submit" v-on:click="choiceFormat()">Select</button>
  </div>
</template>

<script>
export default {
  name: "FormatSelector",
  methods: {
    choiceFormat: function() {
      this.$emit("choiceFormat", this.$refs.format.value)
    }
  }
}
</script>

<style scoped>

</style>
