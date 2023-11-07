<script>
import YummyMeal from "@/components/YummyMeal.vue";
export default {
  components: {YummyMeal},
  setup() {
    const name = "Cheesy Dribbler";
    const placeOrder = () => alert('your order has been placed!')
    const addItem = (item) => alert(`adding ${item} to cart`)

    return {name, placeOrder, addItem}

  }
}

</script>

<template>

  <div class="container">
    <h1>{{name}}</h1>
    <button @click="placeOrder" > Place order</button>
    <YummyMeal name="Burger" @addToCart="addItem" price="5"/>

  </div>


</template>

<style scoped>

.priority {
  color: red;
}

</style>
