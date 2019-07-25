// template can have only one root
<template>
  <div id="app">
    <SearchBar></SearchBar>
  </div>
</template>

<script>
import SearchBar from './components/searchBar.vue'

export default {
//use name for debugging tools
//data, methods and computed go here
  name: 'app',
  components: {
    SearchBar: SearchBar
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
