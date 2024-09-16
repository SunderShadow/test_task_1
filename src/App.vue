<script setup>
import Sidebar from "@/components/Sidebar/index.vue"
</script>

<template>
  <div class="main_container">
    <Sidebar/>
    <main></main>
  </div>
</template>

<style lang="scss" scoped>
.main_container {
  display: flex;
}

main {
  flex-grow: 1;
}
</style>