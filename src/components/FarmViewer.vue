<script setup lang="ts">
defineProps<{ farmName: string }>();
</script>

<template>
  <div
    class="border border-orange-500 border-solid p-4 w-80 h-full flex flex-col items-center justify-center gap-4 shadow"
  >
    <h2>Your farm is called</h2>
    <h1 class="font-bold">{{ farmName || '...' }}</h1>
  </div>
</template>
