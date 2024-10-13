<script setup>
  import Menu from './components/Menu.vue'
  import Header from './components/Header.vue'
  import Filter from './components/Filter.vue'
  
</script>

<template>
  <div class="wrapper">
    <Menu />
    <Header />
    <Filter />
  </div>
</template>

<style scoped>

.wrapper {
  max-width: 1488px;
  margin: auto;
}

</style>
