<script>
import {computed, inject} from "vue";

export default {
  props: {
    price: Number
  },
  setup(props) {
    const currencySymbol = inject('currencySymbol', '$')
    const mealPrice = computed(() => `${currencySymbol.value}${props.price.toFixed(2)}`)
    return {mealPrice}
  }
}
</script>

<template>
<span>{{mealPrice}}</span>
</template>

<style scoped>

</style>