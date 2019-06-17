<template>
  <div id="app">
    <Navbar></Navbar>
    <Index></Index>
  </div>
</template>

<script>
import Index from './components/Index';
import Navbar from './components/Navbar';
export default {
  name: 'app',
  components: {
    Index, Navbar
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
}
</style>
