<template>
  <div class="flex flex-col gap-4">
    <div class="flex gap-2 items-baseline">
      <span>Итого:</span>
      <div class="flex-1 border-b border-dashed"></div>
      <strong>12900 ₽</strong>
    </div>
    <div class="flex gap-2 items-baseline">
      <span>Налог 5%:</span>
      <div class="flex-1 border-b border-dashed"></div>
      <strong>900 ₽</strong>
    </div>
    <button
      disabled=""
      class="mt-4 bg-lime-500 w-full rounded-xl py-3 text-white transition hover:bg-lime-600 active:bg-lime-700 disabled:bg-slate-300"
    >
      Оформить заказ
    </button>
  </div>
</template>
