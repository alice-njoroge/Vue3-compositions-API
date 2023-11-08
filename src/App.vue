<script>
import YummyMeal from "@/components/YummyMeal.vue";
import {reactive, ref, watch} from "vue";
export default {
  components: {YummyMeal},
  setup() {
    const name = ref("Burger King - Munich");
    const cart = reactive([]);
    const meals = reactive([
      {name:"🍔 Cheesy Dribbler", price: 5},
      {name:"🍟 Fries", price: 3},
      {name:"🥕 Impossible burger", price: 7},
    ])
    const placeOrder = () => alert('your order has been placed!')
    const addItem = (item) => cart.push(item);
    // watch(name, (newVal, oldVal) =>  console.log(newVal, oldVal), {immediate:true});
    const removeWatcher = watch(
        [name, ()=> [...cart]],
        (cartNew, cartOld)=>console.log(cartNew, cartOld))
    return {name, placeOrder, addItem, meals, cart, removeWatcher}
  },
}

</script>

<template>

  <div class="container">
    <h1>{{ name }}</h1>

    <button @click="placeOrder"> Place order</button>
    <button @click="removeWatcher"> Remove watcher</button>
    <YummyMeal
        v-for="meal in meals"
        :name="meal.name"
        @addToCart="addItem"
        :price="meal.price"/>

  </div>


</template>

<style scoped>

.priority {
  color: red;
}

</style>
