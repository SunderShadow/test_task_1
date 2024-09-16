<script setup>
import Button        from "@/components/Button.vue"
import IconPlus      from "@/components/icons/IconPlus.vue"
import IconMagnifier from "@/components/icons/IconMagnifier.vue"
import Select        from "@/_page_parts/MainHeader/Select.vue"
import Input         from "@/components/Input.vue"

const search = defineModel('search')
</script>

<template>
<div class="main_header_container">
  <Input placeholder="Search VIN" v-model="search">
    <template v-slot:icon>
      <IconMagnifier />
    </template>
  </Input>

  <Select @change="$emit('cardsPerPage:change', $event.target.value)"/>

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
  width: 350px;
}


.add_vechicle_btn {
  margin-left: auto;
  font-size: .75rem;
}
</style>