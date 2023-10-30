<script setup>
import {reactive, ref} from "vue";

const header = ref('Shopping Portal');
const newItem = ref('');
const editing = ref(false);
const highPriority = ref(false);

const items = reactive([
  {name: 'pens', highPriority: false, id: 1},
  {name: 'laptops', highPriority: false, id: 2},
  {name: 'books', highPriority: true, id: 3},
])

const addItem = () => {
  items.push({id: items.length + 1, name: newItem.value});
  newItem.value = '';
}

const doEdit = (e)=>{
  editing.value = e;
  newItem.value = '';
}


</script>

<template>

  <div class="container">
    <div class="card m-3">
      <div class=" mx-3 card-title">
        <h2>{{ header }}</h2>
        <button @click="doEdit(false)" class=" mx-2 btn btn-secondary">cancel</button>
        <button @click="doEdit(true)" class="btn btn-primary" >Add Items</button>
      </div>

      <div class="card-body">
        <ul v-if="items.length" v-for="({item, name, highPriority, id}, index ) in items" :key="id">
          <li :class="{ priority: highPriority }" > {{ name }}</li>
        </ul>

        <p v-else> Sorry, Nothing to see here </p>
        <hr>
        <form v-if="editing" @submit.prevent="addItem">
          <h3>Add New </h3>
          <input v-model.trim="newItem" @keyup.enter="addItem"
                 placeholder="add a new item">
          <input class="m-2" v-model="highPriority" type="checkbox">
          <button :disabled="newItem.length < 3" type="submit" class="btn btn-primary m-2"> Add</button>
        </form>
      </div>

    </div>
  </div>


</template>

<style scoped>

.priority {
  color: red ;
}

</style>
