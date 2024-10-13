<script setup>
  defineProps({
    id: String,
    name: String,
    code: String,
    priceNew: String,
    priceOld: String,
    imageItem: String,
    material: Number,

    isInCart: Boolean,
    isInFavourites: Boolean,

    onClickInCart: Function,
    onClickInFavourite: Function
  })

  
</script>

<template>
  <div class="item">
    <div class="image">
      <div class="sale" v-if="priceOld !== null">
        <span>Скидка</span>
      </div>
      <img :src="imageItem" alt="Фото товара">
    </div>

    <div class="info">
      <div>
        <p class="code">{{ code }}</p>
        <p class="name_of_item">{{ name }}</p>
        <div class="price"><span class="old">{{ priceOld ? priceOld+'₽' : null}}</span><span class="new">{{ priceNew }}₽</span></div>
      </div>
      <div class="card_icons">
        <img @click="onClickInCart" :src="isInCart ? '/icons/added.png' : '/icons/cart.png'" alt="">
        <img @click="onClickInFavourite" :src="isInFavourites ? '/icons/heart_pink.png' : '/icons/heart_black.png'" alt="">
      </div>
    </div>
  </div>
</template>

<style>
  @import url('https://fonts.cdnfonts.com/css/sf-ui-text-2');
  @import url('https://fonts.cdnfonts.com/css/sf-pro-display');

  .item {
    max-width: 336px;
    min-width: 320px;
    border: 1px solid #EEEEEE;
  }

  .image {
    width: 100%;
    text-align: center;
  }

  .sale {
    width: 81px;
    height: 24px;
    background-color: #EB5757;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-top: 8px;
  }

  .sale span {
    font-family: 'SF Pro Display', sans-serif;
    color: #ffffff;
    font-weight: 500;
    font-size: 14px;
  }

  .info {
    padding-right: 12px;
    padding-left: 12px;
    padding-bottom: 12px;
  }

  .info div {
    width: 50%;
    font-family: 'SF UI Text', sans-serif;
    display: inline-block;
  }

  .code {
    color: #888888;
    font-weight: 400;
    font-size: 10px;
  }

  .name_of_item {
    color: #000000;
    font-weight: 500;
    font-size: 16px;
  }

  .old{
    color: #888888;
    text-decoration: line-through;
    margin-right: 9px;
  }

  .new {
    color: #000000;
  }

  .card_icons {
    text-align: right;
  }

  .card_icons img {
    margin-left: 25px;
  }

  


  
  
</style>
