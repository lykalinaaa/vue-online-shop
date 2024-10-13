<script setup>
  import ItemCard from './ItemCard.vue';

  defineProps({
    items: Array
  })

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
      />
  </div>
</template>

<style>
  .catalogue {
    width: 100%;
    margin-top: 46px;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 66px;
  }

</style>