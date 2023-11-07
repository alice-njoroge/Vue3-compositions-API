<script>
export default {
  setup() {
    const name = "Cheesy Dribbler";
    const placeOrder = () => alert('your order has been placed!')

    return {name, placeOrder}

  }
}

</script>

<template>

  <div class="container">
    <h1>{{name}}</h1>
    <button @click="placeOrder"> Place order</button>

  </div>


</template>

<style scoped>

.priority {
  color: red;
}

</style>
