<script setup>
import Sidebar    from "@/components/Sidebar/index.vue"
import Header     from "@/components/Header/index.vue"
import MainHeader from "@/_page_parts/MainHeader/index.vue"
import Card       from "@/_page_parts/Card.vue"
</script>

<template>
  <div class="main_container">
    <Sidebar/>
    <main>
      <div class="container">
        <Header />
      </div>

      <hr>

      <div class="main_header container">
        <MainHeader/>
      </div>

      <div class="cards">
        <Card />
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

.main_header {
  margin-top: 2rem;
}
</style>