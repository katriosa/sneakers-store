<script setup>
import MainHeader from './components/MainHeader.vue'
import CardList from './components/CardList.vue'
import CartDrawer from './components/CartDrawer.vue'
</script>

<template>
  <CartDrawer />
  <div class="bg-white w-4/5 m-auto mt-14 rounded-xl shadow-xl">
    <MainHeader />

    <div class="p-10">
      <h2 class="text-3xl font-bold mb-8">Все кроссовки</h2>
      <CardList />
    </div>
  </div>
</template>
