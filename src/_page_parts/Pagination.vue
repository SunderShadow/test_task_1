<script setup>
import Input from "@/components/Input.vue"
import IconChevron from "@/components/icons/IconChevron.vue"

const model = defineModel()

defineProps({
  cardPerPage: {
    required: true,
    type: Number
  },
  cardsLength: {
    required: true,
    type: Number
  }
})
</script>

<template>
  <div class="pagination-container">
    Showing {{ cardPerPage }} out of {{ cardsLength }}

    <div class="pagination">
      <IconChevron class="back" @click="$emit('update:modelValue', model - 1)"/>

      <Input v-model="model"/>
      of
      <Input :model-value="Math.ceil(cardsLength / cardPerPage)" disabled/>

      <IconChevron class="forward" @click="$emit('update:modelValue', model + 1)"/>
    </div>
  </div>
</template>

<style scoped lang="scss">
.pagination-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.pagination {
  display: flex;
  align-items: center;
  gap: 1rem;

  .input {
    width: 4ch;
    text-align: center;
  }
}

.back {
  transform: rotate(90deg);
  cursor: pointer;
}

.forward {
  transform: rotate(-90deg);
  cursor: pointer;
}
</style>