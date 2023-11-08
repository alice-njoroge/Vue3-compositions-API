<script>
import YummyMeal from "@/components/YummyMeal.vue";
import {ref, watch} from "vue";
export default {
  components: {YummyMeal},
  setup() {
    const name = ref("Cheesy Dribbler");
    const placeOrder = () => alert('your order has been placed!')
    const addItem = (item) => alert(`adding ${item} to cart`);
    watch(name, (newVal, oldVal) =>  console.log(newVal, oldVal), {immediate:true});

    return {name, placeOrder, addItem}
  },
}

</script>

<template>

  <div class="container">
    <h1>{{ name }}</h1>
    <input v-model="name">
    <button @click="placeOrder"> Place order</button>
    <YummyMeal name="Burger" @addToCart="addItem" :price="5"/>

  </div>


</template>

<style scoped>

.priority {
  color: red;
}

</style>
