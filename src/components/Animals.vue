<script setup lang="ts">
import { AnimalsNames } from "../types";

// Declare expected slots and their respective expected slot props.
// Slot function return type is currently ignored.
defineSlots<{
  horse?: (props: { label?: AnimalsNames }) => any;
  dog?: (props: { label?: AnimalsNames }) => any;
  cat?: (props: { label?: AnimalsNames }) => any;
}>();
</script>

<template>
  <div
    class="border border-blue-500 border-solid p-4 w-80 h-40 flex flex-col items-center justify-center gap-4 shadow"
  >
    <h1 class="font-bold">Animals' names</h1>

    <div>
      <slot name="horse" :label="AnimalsNames.Horse">Horse's name</slot>
    </div>
    <div>
      <slot name="dog" :label="AnimalsNames.Dog"></slot>
    </div>
    <div>
      <slot name="cat" :label="AnimalsNames.Cat"></slot>
    </div>
  </div>
</template>
