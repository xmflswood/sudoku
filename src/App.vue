<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <sudoku></sudoku>
  </div>
</template>

<script>
import sudoku from './components/sudoku.vue'

export default {
  name: 'app',
  components: {
    sudoku
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
