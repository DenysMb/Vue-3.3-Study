<script setup lang="ts">
import { ref, toRef, toValue } from "vue";

const props = defineProps<{ title: string }>();

const titleGetter = toRef(() => props.title);

const counterAsRef = ref(0);

let counterAsValue = toValue(counterAsRef);

// This WILL re-render the component.
const onCounterAsRefChange = () => {
  console.log("Counter As Ref", counterAsRef.value);

  counterAsRef.value++;
};

// This WONT re-render the component.
const onCounterAsValueChange = () => {
  console.log("Counter As Value", counterAsValue);

  counterAsValue++;
};
</script>

<template>
  <div
    class="border border-teal-500 border-solid p-4 w-80 h-40 flex flex-col items-center justify-center gap-2 shadow"
  >
    <h1 class="font-bold">{{ titleGetter }}</h1>

    <p>
      Ref: <strong>{{ counterAsRef }}</strong> Value:
      <strong>{{ counterAsValue }}</strong>
    </p>

    <button
      class="bg-teal-500 hover:bg-teal-700 text-white font-bold py-1 px-2 rounded shadow"
      @click="onCounterAsRefChange"
    >
      Increase Counter As Ref
    </button>
    <button
      class="bg-teal-500 hover:bg-teal-700 text-white font-bold py-1 px-2 rounded shadow"
      @click="onCounterAsValueChange"
    >
      Increase Counter As Value
    </button>
  </div>
</template>
