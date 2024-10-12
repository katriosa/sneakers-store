<template>
  <Drawer
    v-if="drawerOpen"
    :totalPrice="totalPrice"
    :vatPrice="vatPrice"
    :cartButtonDisabled="cartButtonDisabled"
  />
  <div class="bg-white w-4/5 m-auto mt-14 rounded-xl shadow-xl">
    <MainHeader :totalPrice="totalPrice" @openDrawer="openDrawer" />

    <div class="p-10">
      <router-view></router-view>
    </div>
  </div>
</template>

<script setup>
import { ref, watch, provide, computed } from 'vue'
import axios from 'axios'

import MainHeader from './components/MainHeader.vue'
import Drawer from './components/drawer/Drawer.vue'

// Cart (start)
const cart = ref([])
const drawerOpen = ref(false)
const isCreatingOrder = ref(false)

const totalPrice = computed(() => cart.value.reduce((acc, item) => acc + item.price, 0))
const vatPrice = computed(() => Math.round((totalPrice.value * 5) / 100))
const cartIsEmpty = computed(() => cart.value.length === 0)

const cartButtonDisabled = computed(() => isCreatingOrder.value || cartIsEmpty.value)

const closeDrawer = () => {
  drawerOpen.value = false
}
const openDrawer = () => {
  drawerOpen.value = true
}

const addToCart = (item) => {
  cart.value.push(item)
  item.isAdded = true
}

const removeFromCart = (item) => {
  cart.value.splice(cart.value.indexOf(item), 1)
  item.isAdded = false
}

const createOrder = async () => {
  try {
    isCreatingOrder.value = true
    const { data } = await axios.post(`https://0e996b8e15f4603f.mokky.dev/orders`, {
      items: cart.value,
      totalPrice: totalPrice.value
    })

    cart.value = []

    return data
  } catch (err) {
    console.log(err)
  } finally {
    isCreatingOrder.value = false
  }
}
// Cart (end)

watch(
  cart,
  () => {
    localStorage.setItem('cart', JSON.stringify(cart.value))
  },
  { deep: true }
)

provide('cart', {
  cart,
  closeDrawer,
  openDrawer,
  addToCart,
  removeFromCart
})
provide('createOrder', createOrder)
</script>
