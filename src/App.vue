<template>
  <main>
    <h1>{{ header }}</h1>
    <input
      v-model.lazy.trim="userInput"
      type="text"
      placeholder="35 pints of ice cream"
    />

    <label>
      <input v-model="isHighPriority" type="checkbox" />
      High Priority
    </label>

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
</script>
