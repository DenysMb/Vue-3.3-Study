<script setup lang="ts">
import FarmEditor from "./FarmEditor.vue";
import FarmViewer from "./FarmViewer.vue";
import { ref } from "vue";

const farmName = ref("Happy Farm");
</script>

<template>
  <div
    class="border border-yellow-500 border-solid p-4 h-40 flex items-center justify-center gap-4 shadow"
  >
    <FarmEditor v-model="farmName" />

    <FarmViewer :farmName="farmName" />
  </div>
</template>
