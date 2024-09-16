<script setup>
import IconChevron from "@/components/icons/IconChevron.vue"
import {ref} from "vue";

/**
 *
 * @type {Ref<HTMLSelectElement>}
 */
const select = ref()
</script>

<template>
  <div class="vechicles_select" @click="() => {select.showPicker()}">
    <span>Select vehicles per page:</span>

    <div class="vechicles_select-container">
      <select ref="select">
        <option v-for="i in 8" :value="i">{{i}}</option>
        <option value="9" :selected="true">9</option>
      </select>
      <IconChevron class="chevron" />
    </div>
  </div>
</template>

<style scoped lang="scss">
@use "@/cfg.scss";

.vechicles_select {
  display: flex;
  align-items: center;

  gap: 1rem;

  margin-left: 2rem;

  cursor: pointer;

  .vechicles_select-container {
    display: flex;
    align-items: center;
    gap: 1.5rem;

    padding: .5em 1em .5em .5em;

    border: 1px solid cfg.$light-gray-color;
    border-radius: .5rem;
  }

  select {
    border: none;

    background: none;

    -moz-appearance:none; /* Firefox */
    -webkit-appearance:none; /* Safari and Chrome */
    appearance:none;

    font-size: inherit;
    cursor: inherit;
  }
}
</style>