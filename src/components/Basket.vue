<template>
  <div>
    <p class="basket">{{ resultBasket }}</p>
  </div>
</template>

<script>
export default {
  name: "Price",
  props: {
    resultBasket: String
  }
}
</script>

<style scoped>
.basket {
  font-size: 1.5rem;
}
</style>
