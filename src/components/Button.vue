<script setup>

</script>

<template>
  <div class="btn">
    <slot name="icon"/>
    <button><slot/></button>
  </div>
</template>

<style lang="scss" scoped>
@use "@/cfg.scss";

.btn {
  display: flex;
  align-items: center;
  gap: 1rem;
  color: #fff;

  fill: #fff;
  stroke: #fff;

  border-radius: .5rem;
  background-color: cfg.$primary-color;

  font-weight: 700;
  padding: .5rem 1.25rem;

  letter-spacing: 1px;

  cursor: pointer;
}

button {
  border: none;
  background: none;
  color: inherit;

  font: inherit;
  cursor: inherit;
}
</style>