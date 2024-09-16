<script setup>
import Sidebar    from "@/components/Sidebar/index.vue"
import Header     from "@/components/Header/index.vue"
import MainHeader from "@/_page_parts/MainHeader/index.vue"
import Card       from "@/_page_parts/Card.vue"
import {computed, ref} from "vue";

function shuffleArray(array) {
  for (let i = array.length - 1; i >= 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [array[i], array[j]] = [array[j], array[i]];
  }
  return array
}

const cards = shuffleArray([...Array(180).fill({counter: 17}), ...Array(76).fill({counter: 30})])
const cardPerPage = ref(9);

const page = ref(1)

const visibleCards = computed(() => cards.slice(
    (cardPerPage.value * (page - 1)) + page.value - 1,
    page.value * cardPerPage.value
))

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
        <MainHeader @cardsPerPage:change="cardPerPage = $event.target.value" />
      </div>

      <div class="cards container">
        <Card v-for="card in visibleCards" v-bind="card"/>
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

.cards {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 1.8rem;

  margin-top: 2rem;
}
</style>