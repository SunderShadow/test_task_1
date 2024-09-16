<script setup>
import IconMagnifier from "@/components/icons/IconMagnifier.vue"
defineProps({
  placeholder: {
    default: "",
    type: String
  },
  disabled: {
    default: false,
    type: Boolean
  },
})

const value = defineModel()
</script>

<template>
  <div class="input">
    <input type="text" :placeholder v-model="value" :disabled>

    <slot name="icon"/>
  </div>
</template>

<style lang="scss" scoped>
@use "@/cfg.scss";

.input {
  display: flex;
  align-items: center;

  border: 1px solid cfg.$light-gray-color;
  border-radius: .5rem;

  width: 100%;
  padding: .5em;

  input {
    width: 100%;

    border: none;
    outline: none;
    background: transparent;
  }
}
</style>