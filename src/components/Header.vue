<template>
  <div class="header">
    <h1 class="title">Cash Register</h1>
    <h2 class="subtitle">{{ symbol }}</h2>
  </div>
</template>

<script>
export default {
  name: "Header",
  props: {
    symbol: String
  }
}
</script>

<style scoped>
.header {
  width: 100%;
  padding-top: 15px;
  padding-bottom: 15px;
}
.title {
  font-size: 2rem;
  font-weight: bold;
}
.subtitle {
  font-size: 1.7rem;
}
</style>
