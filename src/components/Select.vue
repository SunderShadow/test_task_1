<script setup>
import IconChevron from "@/components/icons/IconChevron.vue";

defineProps({
  src: {
    required: true,
    type: String
  },
  alt: {
    default: "",
    type: String
  }
})
</script>

<template>
  <div class="select">
    <slot />
    <IconChevron />
  </div>
</template>

<style scoped lang="scss">
.select {
  display: flex;

  align-items: center;
  gap: 1rem;
  font-weight: 500;
  border-radius: 100%;
}
</style>