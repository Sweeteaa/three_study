<template>
  <!-- <ThreeTest/> -->
  <Cube/>
</template>

<script>
// import ThreeTest from './components/ThreeTest.vue'
import Cube from './components/Cube.vue'

export default {
  name: 'App',
  components: {
    // ThreeTest,
    Cube
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
