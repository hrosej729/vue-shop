<template>
  <label for="item-type" class="h2">Filtered Items: {{ checkedTypes }}</label>

  <br />

  <input type="checkbox" id="books" value="Books" v-model="checkedTypes" />
  <label for="books"> Books</label>

  <br />

  <input type="checkbox" id="clothes" value="Clothes" v-model="checkedTypes" />
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

  <input type="checkbox" id="drinks" value="Drinks" v-model="checkedTypes" />
  <label for="drinks"> Sports Drinks</label>
</template>

<script>
export default {
  data() {
    return {
      checkedTypes: []
    }
  }
}
</script>

<style></style>
