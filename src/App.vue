<script setup>
  import Header from './components/Header.vue'
  import Catalogue from './components/Catalogue.vue';
  import { onMounted, ref, watch } from 'vue';
  import axios from 'axios';

  const items = ref([]);
  const old_items = ref([]);
  const materials = ref([]);

  const sortParam = ref('');
  const filterParam = ref('');

  const sortSelect = event => {
    sortParam.value = event.target.value;
  }

  const filterSelect = event => {
    filterParam.value = event.target.value;
  }

  onMounted(async () => {
    try {

      const { data } = await  axios.get('/data/items.json')
      items.value = data
      old_items.value = data
      console.log(old_items.value)
      
    } catch (err) {
      console.log(err)
    }



    try {

      const { data } = await  axios.get('/data/materials.json')
      materials.value = data

    } catch (err) {
      console.log(err)
    }
  
  });  

  
  watch(sortParam, async () => {
    if (sortParam.value == "lowToHigh") items.value.sort((a, b) => a.price.current_price > b.price.current_price ? 1 : -1)
    else if (sortParam.value == "highToLow") items.value.sort((a, b) => a.price.current_price < b.price.current_price ? 1 : -1)
      
  });

  watch(filterParam, async () => {
    items.value = old_items.value
    items.value = items.value.filter((item) => item.material == filterParam.value)
  });

</script>

<template>
  <div class="wrapper">
    <Header />
    
    <div class="filter">
    <div class="choice">
      <p>Сортировать по:</p>
      <select @change="sortSelect">
        <option value="lowToHigh">По возрастанию</option>
        <option value="highToLow">По убыванию</option>
      </select>
    </div>
    <div class="choice"> 
      <p>Материал:</p>
      <select @change="filterSelect">
        <option v-for="material in materials" :key="material.id" :value="material.id">{{ material.name }}</option>
      </select>    
    </div>
  </div>

    <Catalogue :materials="materials" :items="items" />
  </div>
</template>

<style scoped>

.wrapper {
  max-width: 1488px;
  margin: auto;
}

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
