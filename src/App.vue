<script setup lang="ts">
import { ref } from "vue";
import Item from "./components/Item.vue";
import List from "./components/List.vue";
import Switch from "./components/Switch.vue";
import { SwitchOption } from "./types";
import Animals from "./components/Animals.vue";
import Farm from "./components/Farm.vue";
import Panel from "./components/Panel.vue";
import Buttons from "./components/Buttons.vue";

const selectedOptionFromSwitch = ref<SwitchOption | undefined>(undefined);

const onSelectedOptionFromSwitchChange = (option: SwitchOption) => {
  selectedOptionFromSwitch.value = option;
};
</script>

<template>
  <div
    class="h-full flex flex-wrap gap-4 place-items-center place-content-center"
  >
    <Item
      :id="42"
      name="Answer to the Ultimate Question of Life, the Universe, and Everything"
    />

    <List
      title="Animals but 'Dog' selected!"
      :items="['Horse', 'Dog', 'Cat']"
      selected="Dog"
    />

    <Switch
      :selectedOption="selectedOptionFromSwitch"
      @switchOption="onSelectedOptionFromSwitchChange"
    />

    <Animals>
      <template #horse="{ label }">
        Horse's name: <span class="font-bold">{{ label }}</span>
      </template>

      <template #dog="{ label }">
        Dog's name: <span class="font-bold">{{ label }}</span>
      </template>

      <template #cat="{ label }">
        Cats' name: <span class="font-bold">{{ label }}</span>
      </template>
    </Animals>

    <Farm />

    <Panel class="this-class-wont-show-because-of-inherit-attrs-false" />

    <Buttons title="Refs Counter" />
  </div>
</template>

<style scoped>
.this-class-wont-show-because-of-inherit-attrs-false {
  background-color: red;
  border: 5px solid yellow;
  color: yellow
}
</style>
