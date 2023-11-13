<script>

import YummyMealPrice from "@/components/YummyMealPrice.vue";

export default {
  components: {YummyMealPrice},
  props: {
    name: String,
    price: Number,
    currencySymbol: String
  },
  setup(props, {emit}) {
    const addToCart = ()=> emit('addToCart', props.name);

    return {addToCart}

  }

}

</script>

<template>

<div>
  <strong>{{ name}} - </strong>
  <yummy-meal-price :currencySymbol="currencySymbol" :price="price"/>
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