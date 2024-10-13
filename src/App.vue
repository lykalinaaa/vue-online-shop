<script setup>
  import Header from './components/Header.vue'
  import Filter from './components/Filter.vue'
  import Catalogue from './components/Catalogue.vue';
  import { onMounted, ref } from 'vue';
  import axios from 'axios';

  const items = ref([]);

  onMounted(async () => {
    try {
      const { data } = await  axios.get('/data/items.json')
      items.value = data
      
    } catch (err) {
      console.log(err)
    }
  
  });  

</script>

<template>
  <div class="wrapper">
    <Header />
    <Filter />
    <Catalogue :items="items" />
  </div>
</template>

<style scoped>

.wrapper {
  max-width: 1488px;
  margin: auto;
}


</style>
