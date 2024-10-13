<script setup>
  import ItemCard from './ItemCard.vue';

  defineProps({
    items: Array
  })

  const onClickInCart = () => {
    alert('545654')
  }

  const onClickInFavourite = () => {
    alert('1111')
  }
</script>

<template>
  <div class="catalogue">
      <ItemCard 
         v-for="item in items"
         :key="item.id"
         :name="item.name"
         :code="item.code"
         :priceNew="item.price.current_price"
         :priceOld="item.price.old_price"
         :imageItem="item.image.url"
         :material="item.material"
         :onClickInCart="onClickInCart"
         :onClickInFavourite="onClickInFavourite"
      />
  </div>
</template>

<style>
  .catalogue {
    width: 100%;
    margin-top: 46px;
    display: flex;
    flex-wrap: wrap;
    gap: 48px;
  }

</style>