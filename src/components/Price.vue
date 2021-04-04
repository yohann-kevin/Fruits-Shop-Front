<template>
  <div>
    <p class="price">{{ result }}</p>
  </div>
</template>

<script>
export default {
  name: "Price",
  props: {
    result: String
  }
}
</script>

<style scoped>
.price {
  padding: 5px;
  font-size: 1.2rem;
}
</style>
