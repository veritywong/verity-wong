<template>
  <div class="app" ref="app-container">
  <div class="title">Product Listing Page</div>

    <div class="filters">
      <h3>Filters</h3>
      <div>
        <label for="checkbox">In Stock</label>
        <input @click="toggleIsAvailable" type="checkbox" id="checkbox" v-model="checked" />
      </div>
    </div>

    <div class="product-grid">
      <ul>
        <li v-for="product in itemsToDisplay" :key="product.name">
          <ProductGridItem :img="product.image" :name="product.name" :price="product.price" :/>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import ProductGridItem from './components/ProductGridItem.vue';
import products from './data/products.json';

export default {
  name: 'App',
  components: {
    ProductGridItem,
  },
  props: ['products'],
  data() {
    return {
      products: products,
      isAvailable: false,
    };
  },
  methods: {
    toggleIsAvailable() {
      this.isAvailable = !this.isAvailable
    },
    filterIsAvailable(products) {
      return this.isAvailable ? this.products.filter((item) => item.isAvailable) : products;
    },
  },
  computed: {
    itemsToDisplay() {
      let products = this.products
      return this.filterIsAvailable(products);
    }
  },
};
</script>

<style>
.app {
  max-width: 1024px;
  margin: 0 auto;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  color: #606569;
}

.link {
  color: #3a7f71;
}
</style>
