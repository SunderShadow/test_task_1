<script setup>
import Input from "@/components/Input.vue"
import IconChevron from "@/components/icons/IconChevron.vue"
import {computed} from "vue";

const model = defineModel()

const props = defineProps({
  cardPerPage: {
    required: true,
    type: Number
  },
  cardsLength: {
    required: true,
    type: Number
  }
})

const pageTotal = computed(() => Math.ceil(props.cardsLength / props.cardPerPage))

const emit = defineEmits()
function back() {
  if (model.value - 1 === 0) {
    return
  }

  emit('update:modelValue', model.value - 1)
}

function forward() {
  if (model.value + 1 > pageTotal.value) {
    return
  }

  emit('update:modelValue', model.value + 1)
}
</script>

<template>
  <div class="pagination-container">
    Showing {{ cardPerPage }} out of {{ cardsLength }}

    <div class="pagination">
      <IconChevron class="back" @click="back"/>

      <Input v-model="model"/>
      of
      <Input :model-value="pageTotal" disabled/>

      <IconChevron class="forward" @click="forward"/>
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