<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <cliente :teste="clienteRodrigo"></cliente>
    <cliente :teste="clienteRodrigo"></cliente>
    <cliente :teste="clienteRodrigo"></cliente>
  </div>
</template>

<script>
import Cliente from './components/Cliente.vue'

export default {
  name: 'App',
  components: {
    Cliente
  },
  data(){
    return {
      clienteRodrigo: {
        nome: "Souza",
        sobrenome: "Viturino",
        idade: 16
      }
    }
  },
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
