<script setup>
import {computed, inject, defineProps} from "vue";
const props = defineProps({
  price: Number
})

const currencySymbol = inject('currencySymbol', '$')
const mealPrice = computed(() => `${currencySymbol.value}${props.price.toFixed(2)}`)

</script>

<template>
<span>{{mealPrice}}</span>
</template>

<style scoped>

</style>