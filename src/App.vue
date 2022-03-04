

<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Formulario/>
  </div>
</template>


<script>
//import HelloWorld from './components/HelloWorld.vue'
  import Formulario from './components/Formulario'


export default {
  name: 'App',
  components: {
    Formulario,
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

