<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black opacity-70 z-10"></div>
  <div class="fixed top-0 right-0 bg-white w-96 h-full z-20 p-8 flex flex-col">
    <DrawerHead />
    <CartList />
    <OrderSummary />
  </div>
</template>

<script setup>
import DrawerHead from './DrawerHead.vue'
import CartList from './CartList.vue'
import OrderSummary from './OrderSummary.vue'
</script>
