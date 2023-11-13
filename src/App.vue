<script setup>
import YummyMeal from "@/components/YummyMeal.vue";
import {reactive, ref, watch, provide} from "vue";

const name = ref("Burger King - Munich");
const cart = reactive([]);
const currencySymbol = ref('$')
provide('currencySymbol', currencySymbol)
const meals = reactive([
  {name: "🍔 Cheesy Dribbler", price: 5},
  {name: "🍟 Fries", price: 3},
  {name: "🥕 Impossible burger", price: 7},
])
const placeOrder = () => alert('your order has been placed!')
const addItem = (item) => cart.push(item);
// watch(name, (newVal, oldVal) =>  console.log(newVal, oldVal), {immediate:true});
const removeWatcher = watch(
    () => [...cart],
    (newVal) => {
      alert(newVal.join('\n'))
    }
)

</script>

<template>

  <div class="container">
    <h1>{{ name }}</h1>
    <span>Select an Option</span>
    <select v-model="currencySymbol">
      <option value="$">Dollar($)</option>
      <option value="£">Euro(£)</option>
    </select>

    <button class="button" @click="placeOrder"> Place order</button>
    <button class="button" @click="removeWatcher"> hide Cart</button>
    <YummyMeal
        v-for="meal in meals"
        :name="meal.name"
        @addToCart="addItem"
        :price="meal.price"
    />

  </div>


</template>

<style scoped>

.priority {
  color: red;
}

.button {
  background-color: darkgrey; /* Green */
  border: none;
  color: white;
  padding: 15px 32px;
  margin: 10px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
}

</style>
