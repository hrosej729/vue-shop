<template>
  <transition-group name="products" appear>
    <label for="item-type" class="h1">
      <div class="badge bg-dark">Results: {{ products.length }}</div>
    </label>
    <hr />
    <div
      v-for="item in products"
      :key="item.id"
      id="item-list"
      class="row align-items-center"
    >
      <product-item :item="item" />
    </div>
  </transition-group>
</template>

<script>
import ProductItem from '@/components/ProductItem.vue'
export default {
  props: ['products'],
  components: {
    ProductItem
  }
}
</script>

<style>
.products-enter-active,
.products-leave-active {
  transition: all 0.5s ease-in-out;
}
.products-enter-from {
  opacity: 0;
  transform: translateX(300px);
}
.products-leave-to {
  opacity: 0;
  transform: translateX(-300px);
}
</style>
