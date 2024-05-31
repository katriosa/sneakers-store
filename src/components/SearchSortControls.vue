<template>
  <div class="flex gap-4">
    <select @change="onChangeSelect" class="py-2 px-3 border rounded-md outline-none">
      <option value="name">По названию</option>
      <option value="price">По цене (дешевые)</option>
      <option value="-price">По цене (дорогие)</option>
    </select>

    <div class="relative">
      <img class="absolute left-4 top-3" src="/search.svg" />
      <input
        @input="onChangeSearchInput"
        class="border rounded-md py-2 pl-10 pr-4 outline-none focus:border-gray-400"
        type="text"
        placeholder="Поиск..."
      />
    </div>
  </div>
</template>

<script setup>
defineProps({
  onChangeSelect: Function,
  onChangeSearchInput: Function
})
</script>
