<template>
  <main>
    <h1>{{ header }}</h1>

    <ul>
      <li v-for="{ id, item } in shoppingList" :key="id">{{ item }}</li>
    </ul>
  </main>
</template>

<script setup>
import { ref } from "vue";

const header = ref("Shopping List App");
const shoppingList = ref([
  { id: 1, item: "10 party hats" },
  { id: 2, item: "2 board games" },
  { id: 3, item: "20 cups" },
]);
</script>
