<template>
  <main>
    <div class="header">
      <h1>{{ header }}</h1>
      <button
        v-if="editting"
        @click="() => (editting = false)"
        class="btn"
        type="button"
      >
        Cancel
      </button>
      <button
        v-else
        @click="() => (editting = true)"
        class="btn btn-primary"
        type="button"
      >
        Add Item
      </button>
    </div>

    <form v-if="editting" @submit.prevent="addToList" class="add-item-form">
      <input
        v-model.trim="userInput"
        type="text"
        placeholder="35 pints of ice cream"
      />
      <label>
        <input v-model="isHighPriority" type="checkbox" />
        High Priority
      </label>

      <button
        :disabled="userInput.length < 5"
        type="submit"
        class="btn btn-primary"
      >
        Save Item
      </button>
    </form>

    <p v-if="shoppingList.length <= 0">Nothing to buy yet. Add more items!</p>
    <ul v-else>
      <li
        v-for="item in shoppingList"
        @click="toggleIsPurchased(item)"
        :key="item.id"
        :class="{ strikeout: item.isPurchased, priority: item.isPriority }"
      >
        {{ item.item }}
      </li>
    </ul>
  </main>
</template>

<script setup>
import { ref } from "vue";

const header = ref("Shopping List App");
const editting = ref(false);
const userInput = ref("");
const isHighPriority = ref(false);
const shoppingList = ref([
  { id: 1, item: "10 party hats", isPriority: false, isPurchased: false },
  { id: 2, item: "2 board games", isPriority: false, isPurchased: true },
  { id: 3, item: "20 cups", isPriority: true, isPurchased: false },
]);

function addToList() {
  shoppingList.value.push({
    id: shoppingList.value.length + 1,
    item: userInput.value,
    isPriority: isHighPriority.value,
    isPurchased: false,
  });
  console.log(isHighPriority);

  userInput.value = "";
  isHighPriority.value = false;
}

function toggleIsPurchased(item) {
  item.isPurchased = !item.isPurchased;
}
</script>
