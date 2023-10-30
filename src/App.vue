<script setup>
import {ref} from "vue";

const header = ref('Shopping Portal');
const newItem = ref('');
const highPriority = ref(false);

const items = ref([
  {name: 'pens', id: 1},
  {name: 'laptops', id: 2},
  {name: 'books', id: 3},
])


</script>

<template>

  <h1>{{ header }}</h1>
  <ul v-for="item in items" :key="item.id" >
    <li> {{item.name}} </li>
  </ul>
  <hr>

  <h2>Add New </h2>
  <input v-model.trim="newItem" placeholder="add a new item" >
  <input v-model="highPriority" type="checkbox">
  <br/>
  <button @click="items.push({id:items.length + 1, name: newItem})" class="btn btn-primary"> Add</button>
</template>

<style scoped>

</style>
