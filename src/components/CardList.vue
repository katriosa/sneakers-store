<template>
  <div class="grid grid-cols-4 gap-5 mt-10">
    <CardItem
      v-for="item in items"
      :key="item.id"
      :id="item.id"
      :title="item.title"
      :imageUrl="item.imageUrl"
      :price="item.price"
      :is-added="false"
      :isFavorite="item.isFavorite"
      :onClickAdd="onClickAdd"
      :onClickFavorite="() => addToFavorite(item)"
    />
  </div>
</template>

<script setup>
import CardItem from './CardItem.vue'

defineProps({
  items: Array,
  addToFavorite: Function
})

const onClickAdd = () => {
  alert('Add!')
}
// const onClickFavorite = () => {
//   alert('Like!')
// }

// const onClickFavorite = () => {
//   const obj = {
//     ...props,
//     parentId: props.items.id
//   }
//   props.addToFavorite(obj)
// }
</script>
