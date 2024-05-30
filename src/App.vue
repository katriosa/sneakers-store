<script setup>
import MainHeader from './components/MainHeader.vue'
import CardList from './components/CardList.vue'
import SearchSortControls from './components/SearchSortControls.vue'
// import Drawer from './components/drawer/Drawer.vue'
</script>

<template>
  <!-- <Drawer /> -->
  <div class="bg-white w-4/5 m-auto mt-14 rounded-xl shadow-xl">
    <MainHeader />

    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>
        <SearchSortControls />
      </div>
      <CardList />
    </div>
  </div>
</template>
