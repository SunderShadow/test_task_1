<script setup>
import Sidebar    from "@/components/Sidebar/index.vue"
import Header     from "@/components/Header/index.vue"
import MainHeader from "@/_page_parts/MainHeader/index.vue"
import Card       from "@/_page_parts/Card.vue"

import {ref, watch} from "vue"
import Pagination from "@/_page_parts/Pagination.vue"

const cardPerPage = ref(9);

const page   = ref(1)
const search = ref('')
const cards  = ref([])

const meta = ref({
  last_page: 0,
  total: 0
})

let searchLoadTimeOut

watch(search, () => {
  clearTimeout(searchLoadTimeOut)
  searchLoadTimeOut = setTimeout(() => {
    load()
  }, 300)
})

watch(page, load)
watch(cardPerPage, load)
async function load() {
  const URL = "https://api.caiman-app.de/api/cars-test"

  let data = {
    per_page: cardPerPage.value.toString(),
    page: page.value.toString()
  }

  if (search.value) {
    data.search = search.value.toString()
  }

  fetch(URL + '?' + new URLSearchParams(data).toString(), {
    credentials: 'include'
  })
      .then(data => data.json())
      .then(data => {
        cards.value = data.data
        meta.value = data.meta
      })
}

load()

</script>

<template>
  <div class="main_container">
    <Sidebar/>
    <main>
      <div class="container">
        <Header :vechicles-count="meta.total"/>
      </div>

      <hr>

      <div class="main_header container">
        <MainHeader
            v-model:search="search"
            @cardsPerPage:change="cardPerPage = $event"
        />
      </div>

      <div class="cards container">
        <Card
            v-for="card in cards"
            :name="card.vehicle_name ?? 'Nullname'"
            :uploads="card.uploads"
            :vin="card.vin"
            :img="card?.photo?.url ?? ''"
        />
      </div>

      <div class="pagination container">
        <Pagination :card-per-page="cardPerPage" :cards-length="meta.total" v-model="page"/>
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
  margin-bottom: 3rem;
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

.pagination {
  margin-top: 2rem;
}
</style>