<script setup lang="ts">
// Importing types
import { onMounted } from "vue";
import type { Item } from "../types";

// Destructuring props
const { id, name } = defineProps<Item>();

// Easy access to the destrucutred props
onMounted(() => {
  console.log(`Item ${id} - ${name}`);
});
</script>

<template>
  <div
    class="border border-purple-500 border-solid p-4 w-80 h-40 flex flex-col items-center justify-center gap-4 shadow"
  >
    <h1 class="font-bold">{{ name }}</h1>
    <p>ID: {{ id }}</p>
  </div>
</template>

<style scoped>
</style>
