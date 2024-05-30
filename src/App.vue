<template>
  <!-- <Drawer /> -->
  <div class="bg-white w-4/5 m-auto mt-14 rounded-xl shadow-xl">
    <MainHeader />

    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>
        <SearchSortControls />
      </div>
      <CardList :items="items" />
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

import MainHeader from './components/MainHeader.vue'
import CardList from './components/CardList.vue'
import SearchSortControls from './components/SearchSortControls.vue'
// import Drawer from './components/drawer/Drawer.vue'

const items = ref([])

onMounted(async () => {
  try {
    const { data } = await axios.get('https://0e996b8e15f4603f.mokky.dev/items')
    items.value = data
  } catch (err) {
    console.error(err)
  }
})
</script>
