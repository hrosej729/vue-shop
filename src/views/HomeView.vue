<template>
  <section class="container">
    <div class="row">
      <div class="col-md-3">
        <label for="item-type" class="h1">Filters </label>

        <hr />

        <label for="item-type" class="h3">Product Type:</label>
        <br />
        <input
          type="checkbox"
          id="books"
          value="Books"
          v-model="checkedTypes"
        />
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

        <hr />

        <range-selector :products="filteredProducts" v-model="max" />
      </div>

      <div class="col">
        <product-list :products="filteredProducts" />
      </div>
    </div>
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
      cart: [],
      checkedTypes: []
    }
  },
  props: ['products'],
  components: {
    ProductList,
    RangeSelector
  },
  computed: {
    filteredProducts() {
      let books = this.checkedTypes.includes('Books')
      let clothes = this.checkedTypes.includes('Clothes')
      let vitamins = this.checkedTypes.includes('Vitamins')
      let drinks = this.checkedTypes.includes('Drinks')

      let booksMin = 0
      let booksMax = 0
      let clothesMin = 126
      let vitaMin = 0
      let vitaMax = 0
      let drinkMax = 0
      if (books) {
        booksMin = 24
        booksMax = 25
      }
      if (clothes) {
        clothesMin = 15
      }
      if (vitamins) {
        vitaMin = 5
        vitaMax = 15
      }
      if (drinks) {
        drinkMax = 5
      }
      if (!books && !clothes && !vitamins && !drinks) {
        return this.products.filter(item => item.price < Number(this.max))
      }
      return this.products.filter(
        item =>
          (item.price < Number(this.max) &&
            item.price > booksMin &&
            item.price < booksMax) ||
          (item.price < Number(this.max) &&
            item.price > clothesMin &&
            !(item.price > 24 && item.price < 25)) ||
          (item.price < Number(this.max) &&
            item.price > vitaMin &&
            item.price < vitaMax) ||
          (item.price < Number(this.max) && item.price < drinkMax)
      )
    }
  }
}
</script>
