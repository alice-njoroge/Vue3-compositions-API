<script>
import {computed} from "vue";

export default {
  props: {
    name: String,
    price: Number,
  },
  setup(props, {emit}) {
    const addToCart = ()=> emit('addToCart', props.name);
    const mealPrice = computed(()=> `$${props.price.toFixed(2)}`)
    const priceSentence = computed(
        () => `the price of this item is ${mealPrice.value}`
    )

    return {addToCart, mealPrice, priceSentence}

  }

}

</script>

<template>

<div>
  <strong>{{ name}} - </strong>
<!--  <span>{{priceSentence}}</span> - -->
  <button @click="addToCart">Add to Cart</button>
</div>

</template>

<style scoped>

</style>