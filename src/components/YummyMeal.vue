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
  {{mealPrice}}
<!--  <span>{{priceSentence}}</span> - -->
  <button class="button" @click="addToCart">Add to Cart</button>
</div>

</template>

<style scoped>
.button {
  background-color:  dodgerblue; /* Green */
  border: none;
  color: white;
  padding: 5px 5px ;
  margin: 10px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}

</style>