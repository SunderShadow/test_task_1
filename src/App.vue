<script setup>
import Sidebar from "@/components/Sidebar/index.vue"
import Header  from "@/components/Header/index.vue"
import MainHeader from "@/_page_parts/MainHeader/index.vue";
</script>

<template>
  <div class="main_container">
    <Sidebar/>
    <main>
      <div class="container">
        <Header />
      </div>
      <hr class="divider">

      <div class="main_header container">
        <MainHeader/>
      </div>
    </main>
  </div>
</template>

<style lang="scss" scoped>
.main_container {
  display: flex;
}

main {
  flex-grow: 1;
}

.container {
  padding: 0 30px;
}

.divider {
  background-color: #E4E4E4;
  margin: 0;
}

.main_header {
  margin-top: 2rem;
}
</style>