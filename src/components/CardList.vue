<template>
  <div class="grid grid-cols-4 gap-5 mt-10">
    <CardItem
      v-for="item in items"
      :key="item.id"
      :id="item.id"
      :title="item.title"
      :imageUrl="item.imageUrl"
      :price="item.price"
      :isAdded="item.isAdded"
      :isFavorite="item.isFavorite"
      :onClickFavorite="() => addToFavorite(item)"
      :onClickAdd="() => addToCart(item)"
    />
  </div>
</template>

<script setup>
import CardItem from './CardItem.vue'

defineProps({
  items: Array,
  addToFavorite: Function,
  addToCart: Function
})
</script>
