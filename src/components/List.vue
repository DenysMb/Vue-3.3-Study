<script setup lang="ts" generic="T">
// Importing interface
import type { List } from "../types";

defineProps<List<T> & { title: string }>();
</script>

<template>
  <div class="border border-red-500 border-solid p-4 w-80 h-40 flex flex-col items-center justify-center gap-4 shadow">
    <h1 class="font-bold">{{ title }}</h1>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        <span :class="{ 'text-green-500 font-bold': selected === item }">{{ item }}</span>
      </li>
    </ul>
  </div>
</template>

<style scoped></style>
