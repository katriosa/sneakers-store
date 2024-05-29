<template>
  <div class="grid grid-cols-4 gap-5">
    <CardItem
      title="Мужские Кроссовки Nike Blazer Mid Suede"
      imageUrl="/sneakers/sneakers-1.jpg"
      :price="1205"
      :is-added="false"
      :is-favorite="false"
      :onClickAdd="onClickAdd"
      :onClickFavorite="onClickFavorite"
    />
  </div>
</template>

<script setup>
import CardItem from './CardItem.vue'

const onClickAdd = () => {
  alert('Add!')
}
const onClickFavorite = () => {
  alert('Like!')
}
</script>
