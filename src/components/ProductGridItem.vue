<template>
  <div class="product-grid-item product-container">
    <img class="product-image" :src="img" />
    <p class="product-name">{{ name }}</p>
    <p class="product-price">£{{ price }}</p>
  </div>
</template>

<script>
export default {
  name: 'ProductGridItem',
  // props: {
  //   product: { type: Object, required: true, default: () => ({}) },
  // },
  props: ['img', 'name', 'price'],
};
</script>

<style scoped>
.product-grid-item {
  background: #ddebe8;
  max-width: 150px;
}

.product-image {
  width: 100%;
}
</style>
