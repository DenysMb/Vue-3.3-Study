<script setup lang="ts">
import { watchEffect } from "vue";

const farm = defineModel();

watchEffect(() => {
  console.log("Farm Value", farm.value);
});
</script>

<template>
  <div
    class="border border-amber-500 border-solid p-4 w-72 h-full flex flex-col items-center justify-center gap-4 shadow"
  >
    <h1 class="font-bold">What's your farm name?</h1>

    <div class="input">
      <input
        class="border border-amber-500 px-1 shadow"
        v-model="farm"
        placeholder="Farm name"
      />
    </div>
  </div>
</template>

<style scoped>
.input {
  position: relative;
}

.input:after {
  content: "🔤";
  position: absolute;
  top: 0;
  right: 5px;
  height: 100%;
  display: flex;
  align-items: center;
  filter: hue-rotate(180deg);
}
</style>
