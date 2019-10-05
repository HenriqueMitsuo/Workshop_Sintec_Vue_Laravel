<template>
  <div id="app">
    <Home/> 
    <Table/>
  </div>
</template>

<script>
import Home from './components/Home.vue'
import Table from './components/Table.vue'

export default {
  name: 'app',
  components: {
    Home,
    Table,
  }
}
</script>

<style>

</style>
