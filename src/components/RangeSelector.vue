<template>
  <label for="max-price" class="form-label h3"
    >Max Price: ${{ modelValue }}</label
  >

  <input
    type="range"
    class="form-range"
    min="0"
    max="130"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>

<script>
export default {
  props: ['products', 'modelValue']
}
</script>

<style></style>
