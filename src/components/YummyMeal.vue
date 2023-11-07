<script>
export default {
  props: {
    name: String,
    price: Number,
  },
  setup(props, {emit}) {
    const addToCart = ()=> emit('addToCart', props.name);

    return {addToCart}

  }

}

</script>

<template>

<div>
  <strong> 🍔- {{ name}}</strong>
  {{price}}
  <button @click="addToCart">Add to Cart</button>
</div>

</template>

<style scoped>

</style>