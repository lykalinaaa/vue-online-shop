<script setup>
  defineProps({
    materials: Array,
    materialList: {
      type: String,
      default: '0',
    },
  })

</script>

<template>
  <div class="filter">
    <div class="choice">
      <p>Сортировать по:</p>
      <select>
        <option value="0" selected>Без сортировки</option>
        <option value="1">По возрастанию</option>
        <option value="2">По убыванию</option>
      </select>
    </div>
    <div class="choice"> 
      <p>Материал:</p>
      <select 
      :value="materialList"
      @input="$emit('update:modelValue', $event.target.value)">
        <option value="0">Все материалы</option>
        <option v-for="material in materials" :key="material.id" :value="material.id">{{ material.name }}</option>
      </select>    
    </div>
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

  

</style>