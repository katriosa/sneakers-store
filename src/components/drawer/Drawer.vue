<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black opacity-70 z-10"></div>
  <div class="fixed top-0 right-0 bg-white w-96 h-full z-20 p-8 flex flex-col">
    <DrawerHead />
    <div v-if="!totalPrice || orderId" class="flex h-full items-center">
      <InfoBlock
        v-if="orderId"
        title="Заказ оформлен!"
        :description="`Ваш заказ #${orderId} скоро будет передан курьерской доставке.`"
        imageUrl="/order-success-icon.png"
      />
      <InfoBlock
        v-else
        title="Корзина пустая"
        description="Добавьте хотя бы одну пару кроссовок, чтобы сделать заказ."
        imageUrl="/package-icon.png"
      />
    </div>
    <div v-else>
      <CartList />
      <OrderSummary
        :totalPrice="totalPrice"
        :vatPrice="vatPrice"
        :buttonDisabled="buttonDisabled"
      />
    </div>
  </div>
</template>

<script setup>
import { ref, provide, inject, computed } from 'vue'
import axios from 'axios'

import DrawerHead from './DrawerHead.vue'
import CartList from './CartList.vue'
import OrderSummary from './OrderSummary.vue'
import InfoBlock from './InfoBlock.vue'

const props = defineProps({
  totalPrice: Number,
  vatPrice: Number
})

const { cart } = inject('cart')

const cartIsEmpty = computed(() => cart.value.length === 0)
const buttonDisabled = computed(() => isCreatingOrder.value || cartIsEmpty.value)

const isCreatingOrder = ref(false)
const orderId = ref(null)

const createOrder = async () => {
  try {
    isCreatingOrder.value = true
    const { data } = await axios.post(`https://0e996b8e15f4603f.mokky.dev/orders`, {
      items: cart.value,
      totalPrice: props.totalPrice.value
    })

    cart.value = []
    orderId.value = data.id
    // return data
  } catch (err) {
    console.log(err)
  } finally {
    isCreatingOrder.value = false
  }
}

provide('createOrder', createOrder)
</script>
