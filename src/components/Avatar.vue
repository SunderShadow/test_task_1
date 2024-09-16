<script setup>
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
  <div class="avatar">
    <img :src :alt>

    <span><slot /></span>
  </div>
</template>

<style scoped lang="scss">
.avatar {
  display: flex;

  align-items: center;
  gap: 1rem;
  font-weight: 500;
  border-radius: 100%;
}
</style>