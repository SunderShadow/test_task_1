<script setup>
defineProps({
  active: {
    default: false,
    type: Boolean
  }
})
</script>

<template>
  <div class="container" :class="{active}">
    <div class="icon">
      <slot name="icon"/>
    </div>
    <span><slot/></span>
  </div>
</template>

<style lang="scss" scoped>
@use "@/cfg";

.container {
  position: relative;

  display: flex;
  align-items: center;
  gap: 1.25rem;

  padding: .75rem 2rem;

  font-weight: 500;

  opacity: .45;

  transition-property: opacity;
  transition-duration: 200ms;

  cursor: pointer;

  &::after {
    content: "";

    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;

    width: 2px;

    background-color: cfg.$primary-color;

    opacity: 0;

    transition-property: opacity;
    transition-duration: inherit;
  }

  &::before {
    --bg-opacity: 0;

    content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;

    transition-property: background;
    transition-duration: inherit;

    background-color: rgba(#fff, var(--bg-opacity));
  }

  &:hover {
    opacity: .75;

    &::before {
      --bg-opacity: .2;
    }
  }

  &.active {
    opacity: 1;

    &::after {
      opacity: 1;
    }

    &::before {
      --bg-opacity: .2;
    }
  }
}

.icon {
  height: 1.5rem;
}
</style>