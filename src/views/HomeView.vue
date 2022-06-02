<template>
  <section class="container">
    <div>
      <label for="item-type" class="h2"
        >Filtered Items: {{ checkedTypes }}</label
      >

      <br />

      <input type="checkbox" id="books" value="Books" v-model="checkedTypes" />
      <label for="books"> Books</label>

      <br />

      <input
        type="checkbox"
        id="clothes"
        value="Clothes"
        v-model="checkedTypes"
      />
      <label for="clothes"> Clothes</label>

      <br />

      <input
        type="checkbox"
        id="vitamins"
        value="Vitamins"
        v-model="checkedTypes"
      />
      <label for="vitamins"> Vitamins</label>

      <br />

      <input
        type="checkbox"
        id="drinks"
        value="Drinks"
        v-model="checkedTypes"
      />
      <label for="drinks"> Sports Drinks</label>
    </div>

    <range-selector :products="filteredProducts" v-model="max" />
    <product-list :products="filteredProducts" />
  </section>
</template>

<script>
import ProductList from '@/components/ProductList'
import RangeSelector from '@/components/RangeSelector'

export default {
  name: 'HomeView',

  data: function () {
    return {
      max: 50,
      cart: []
    }
  },
  props: ['products'],
  components: {
    ProductList,
    RangeSelector
  },
  computed: {
    filteredProducts() {
      return this.products.filter(item => item.price < Number(this.max))
    }
  }
}
</script>
