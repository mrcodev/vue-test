<template>
  <div id="app">

    <Schematic msg="This is test for Vue.js Developer "/>
  </div>
</template>

<script>

import Schematic from './components/Schematic.vue'


export default {
  name: 'app',
  components: {
    Schematic
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
  background-color: aliceblue;
  padding: 1rem;
}
  * {
    box-sizing: border-box;
  }
  .flexBox {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
  }
</style>
