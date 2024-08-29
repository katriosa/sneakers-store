<template>
  <div class="flex items-center gap-4 border border-slate-100 p-4 rounded-xl">
    <img class="w-16 h-16" :src="imageUrl" alt="Sneakers" />
    <div class="flex flex-col flex-1">
      <p>{{ title }}</p>
      <div class="flex justify-between mt-2">
        <strong class="flex-1">{{ price }} ₽</strong>
        <img
          @click="emit('onClickRemove')"
          class="opacity-40 hover:opacity-100 cursor-pointer transition"
          src="/close.svg"
          alt="Close Icon"
        />
      </div>
    </div>
  </div>
</template>

<script setup>
const emit = defineEmits(['onClickRemove'])

defineProps({
  id: Number,
  title: String,
  imageUrl: String,
  price: Number
})
</script>
