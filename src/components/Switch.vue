<script setup lang="ts">
import { SwitchOption } from "../types";

// With destructure you can easily set a default value
const { selectedOption = "Cat 😺" } = defineProps<{
  selectedOption?: SwitchOption;
}>();

// Now  you can declare emits with type literal.
// You can use the labeled tuple elements for explicitness.
const emit = defineEmits<{
  switchOption: [options: string];
}>();

const onSwitchOptionChange = (event: Event) => {
  const { checked } = <HTMLInputElement>event?.target;

  emit("switchOption", checked ? SwitchOption.Dog : SwitchOption.Cat);
};
</script>

<template>
  <div
    class="border border-green-500 border-solid p-4 w-80 h-40 flex flex-col items-center justify-center gap-4 shadow"
  >
    <h1 class="font-bold">
      Cool 'Switch' to test new
      <code class="p-1 font-thin bg-opacity-50">defineEmits</code>
    </h1>

    <p>
      The selected option is:
      <span class="font-bold">{{ selectedOption }}</span>
    </p>

    <div class="flex items-center gap-2">
      <label class="switch">
        <input type="checkbox" @change="onSwitchOptionChange($event)" />
        <span class="slider shadow" />
        <span class="symbols" />
      </label>
    </div>
  </div>
</template>

<style scoped>
.switch {
  width: 64px;
  height: 32px;
  display: inline-block;
  position: relative;
}

.switch input {
  opacity: 0;
  width: 0;
  height: 0;
}
.slider {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  border-radius: 32px;
  cursor: pointer;
  background-color: rgb(203 213 225);
  -webkit-transition: 0.5s;
  transition: 0.5s;
}

.slider:before {
  border-radius: 50%;
  position: absolute;
  content: "🤍";
  height: 24px;
  width: 24px;
  left: 4px;
  bottom: 4px;
  background-color: white;
  -webkit-transition: 0.5s;
  transition: 0.5s;
  z-index: 10;
}

input:checked + .slider {
  background-color: rgb(34 197 94);
}

input:checked + .slider:before {
  -webkit-transform: translateX(32px);
  -ms-transform: translateX(32px);
  transform: translateX(32px);
}

.symbols:before {
  content: "🐶";
  position: absolute;
  top: 0;
  left: 0;
  width: 32px;
  height: 32px;
  z-index: 5;
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: 0.5s;
}

.symbols:after {
  content: "😺";
  position: absolute;
  top: 0;
  right: 0;
  width: 32px;
  height: 32px;
  z-index: 5;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: 0.5s;
}

input:checked ~ .symbols:after {
  opacity: 0;
  transition: 0.5s;
}

input:checked ~ .symbols:before {
  opacity: 1;
  transition: 0.5s;
}
</style>
