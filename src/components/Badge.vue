<script setup>

</script>

<template>
  <span class="badge">
    <span><slot/></span>
  </span>
</template>

<style scoped lang="scss">
.badge {
  padding: .25em .85em;
  border-radius: .4em;

  background-color: #F3F6F8;

  line-height: 1.5em;
  font-weight: 700;

  span {
    opacity: .8;
  }
}
</style>