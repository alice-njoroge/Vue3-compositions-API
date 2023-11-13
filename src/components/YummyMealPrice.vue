<script>
import {computed} from "vue";

export default {
  props: {
    currencySymbol: String,
    price: Number
  },
  setup(props) {
    const mealPrice = computed(() => `${props.currencySymbol}${props.price.toFixed(2)}`)
    return {mealPrice}
  }
}
</script>

<template>
<span>{{mealPrice}}</span>
</template>

<style scoped>

</style>