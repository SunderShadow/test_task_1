<script setup>
defineProps({
  type: {
    default: 'default',
    type: String
  }
})
</script>

<template>
  <span class="badge" :class="type">
    <span><slot/></span>
  </span>
</template>

<style scoped lang="scss">
@use "@/cfg.scss";

.badge {
  padding: .25em .85em;
  border-radius: .4em;

  background-color: #F3F6F8;

  line-height: 1.5em;
  font-weight: 700;

  span {
    opacity: .8;
  }

  &.success {
    color: cfg.$secondary-color;
    stroke: cfg.$secondary-color;
    background-color: #E4F5DD;
  }
}
</style>