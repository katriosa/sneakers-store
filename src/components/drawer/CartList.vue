<template>
  <div class="flex flex-col flex-1 gap-4">
    <CartItem
      v-for="item in cart"
      :key="item.id"
      :id="item.id"
      :title="item.title"
      :imageUrl="item.imageUrl"
      :price="item.price"
      @onClickRemove="() => removeFromCart(item)"
    />
  </div>
</template>

<script setup>
import CartItem from './CartItem.vue'
import { inject } from 'vue'

const { cart, removeFromCart } = inject('cart')
</script>
