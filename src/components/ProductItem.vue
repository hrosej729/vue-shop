<template>
  <div class="col-2 m-auto">
    <button
      @click="this.$parent.$parent.$parent.$parent.$emit('addItem', item)"
      class="btn btn-success"
    >
      +
    </button>
  </div>
  <div class="col-sm-4">
    <img class="img-fluid d-block" :src="item.image" :alt="item.name" />
  </div>
  <div class="col">
    <h3 class="text-primary">{{ item.name }}</h3>
    <p class="mb-0">{{ item.description }}</p>
    <div class="h5 float-right">
      <span class="badge bg-info" v-if="item.price > 24 && item.price < 25"
        >book</span
      >
      <span class="badge bg-success" v-else-if="item.price > 15">clothing</span>
      <span class="badge bg-primary" v-else-if="item.price > 5">vitamin</span>
      <span class="badge bg-danger" v-else>sports drink</span>
      <span class="label"></span><curr-values :amt="item.price"></curr-values>
    </div>
  </div>
</template>

<script>
import CurrValues from './CurrValues.vue'
export default {
  components: { CurrValues },
  props: ['item'],
  emits: ['addItem']
}
</script>

<style></style>
