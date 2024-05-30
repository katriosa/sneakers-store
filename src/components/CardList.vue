<template>
  <div class="grid grid-cols-4 gap-5 mt-10">
    <CardItem
      v-for="item in items"
      :key="item.id"
      :title="item.title"
      :imageUrl="item.imageUrl"
      :price="item.price"
      :is-added="false"
      :is-favorite="false"
      :onClickAdd="onClickAdd"
      :onClickFavorite="onClickFavorite"
    />
  </div>
</template>

<script setup>
import CardItem from './CardItem.vue'

defineProps({
  items: Array
})

const onClickAdd = () => {
  alert('Add!')
}
const onClickFavorite = () => {
  alert('Like!')
}
</script>
