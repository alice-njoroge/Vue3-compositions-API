<script setup>
import {defineEmits} from 'vue'

const props = defineProps({
  name: String,
  price: Number,
})

const emit = defineEmits(['addToCart'])

import YummyMealPrice from "@/components/YummyMealPrice.vue";
const addToCart = ()=> emit('addToCart', props.name);


</script>

<template>

<div>
  <strong>{{ name}} - </strong>
  <yummy-meal-price :price="price"/>
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