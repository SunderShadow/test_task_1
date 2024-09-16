<script setup>

import IconMagnifier from "@/components/icons/IconMagnifier.vue"
import Button from "@/components/Button.vue"
import IconPlus from "@/components/icons/IconPlus.vue"
import Select from "@/_page_parts/MainHeader/Select.vue"

</script>

<template>
<div class="main_header_container">
  <div class="input">
    <input type="text" placeholder="Search VIN">

    <IconMagnifier/>
  </div>

  <Select />

  <Button class="add_vechicle_btn">
    <template v-slot:icon><IconPlus/></template>
    <span>ADD VECHICLE</span>
  </Button>
</div>
</template>

<style lang="scss" scoped>
@use "@/cfg";

.main_header_container {
  display: flex;
}

.input {
  display: flex;
  align-items: center;

  border: 1px solid cfg.$light-gray-color;
  border-radius: .5rem;

  width: 350px;
  padding: .5em;

  input {
    width: 100%;

    border: none;
    outline: none;
    background: transparent;
  }
}

.add_vechicle_btn {
  margin-left: auto;
  font-size: .75rem;
}
</style>