<template>
  <div class="flex flex-col gap-4">
    <div class="flex gap-2 items-baseline">
      <span>Итого:</span>
      <div class="flex-1 border-b border-dashed"></div>
      <strong>{{ totalPrice }} ₽</strong>
    </div>
    <div class="flex gap-2 items-baseline">
      <span>Налог 5%:</span>
      <div class="flex-1 border-b border-dashed"></div>
      <strong>{{ vatPrice }} ₽</strong>
    </div>
    <button
      :disabled="buttonDisabled"
      @click="createOrder"
      class="mt-4 bg-lime-500 w-full rounded-xl py-3 text-white transition hover:bg-lime-600 active:bg-lime-700 disabled:bg-slate-300"
    >
      Оформить заказ
    </button>
  </div>
</template>
<script setup>
import { inject } from 'vue'

defineProps({
  totalPrice: Number,
  vatPrice: Number,
  buttonDisabled: Boolean
})

const createOrder = inject('createOrder')
</script>
