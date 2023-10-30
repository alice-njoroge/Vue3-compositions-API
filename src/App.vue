<script setup>
import {reactive, ref} from "vue";

const header = ref('Shopping Portal');
const newItem = ref('');
const highPriority = ref(false);

const items = reactive([
  // {name: 'pens', id: 1},
  // {name: 'laptops', id: 2},
  // {name: 'books', id: 3},
])

const addItem = () => {
  items.push({id: items.length + 1, name: newItem.value});
  newItem.value = '';
}


</script>

<template>

  <div class="container">
    <div class="card m-3">
      <div class=" mx-3 card-title">
        <h2>{{ header }}</h2>
      </div>

      <div class="card-body">
        <ul v-if="items.length" v-for="item in items" :key="item.id">
          <li> {{ item.name }}</li>
        </ul>

        <p v-else> Sorry, Nothing to see here </p>
        <hr>
        <form @submit.prevent="addItem">
          <h3>Add New </h3>
          <input v-model.trim="newItem" @keyup.enter="addItem"
                 placeholder="add a new item">
          <input class="m-2" v-model="highPriority" type="checkbox">
          <button type="submit" class="btn btn-primary m-2"> Add</button>
        </form>
      </div>

    </div>
  </div>


</template>

<style scoped>

</style>
