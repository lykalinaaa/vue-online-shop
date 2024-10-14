<script setup>
  import ItemCard from './ItemCard.vue';

  defineProps({
    items: Array,
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
  @import url('https://fonts.cdnfonts.com/css/sf-pro-display');

  .filter {
    display: flex;
    flex-wrap: wrap;
    top: 160px;
    font-family: 'SF Pro Display', sans-serif;
    gap: 24px;
  }

  .choice p{
    margin-left: 16px;
    color: #4F4F4F;
    font-size: 12px;
    font-weight: 400;
  }

  .choice select {
    background-color: #F2F2F2;
    width: 288px;
    height: 40px;
    border: none;
    padding-left: 13px;
    font-family: 'SF Pro Display', sans-serif;
    font-size: 14px;
  }

  .catalogue {
    width: 100%;
    margin-top: 46px;
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 66px;
  }

</style>