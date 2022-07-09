<template>
  <main>
    <h1>{{ header }}</h1>
    <form @submit.prevent="addToList" class="add-item-form">
      <input
        v-model.trim="userInput"
        type="text"
        placeholder="35 pints of ice cream"
      />
      <label>
        <input v-model="isHighPriority" type="checkbox" />
        High Priority
      </label>

      <button type="submit" class="btn btn-primary">Save Item</button>
    </form>

    <ul>
      <li v-for="{ id, item } in shoppingList" :key="id">{{ item }}</li>
    </ul>
  </main>
</template>

<script setup>
import { ref } from "vue";

const header = ref("Shopping List App");
const userInput = ref("");
const isHighPriority = ref(false);
const shoppingList = ref([
  { id: 1, item: "10 party hats" },
  { id: 2, item: "2 board games" },
  { id: 3, item: "20 cups" },
]);

function addToList() {
  shoppingList.value.push({
    id: shoppingList.value.length + 1,
    item: userInput.value,
  });

  userInput.value = "";
}
</script>
