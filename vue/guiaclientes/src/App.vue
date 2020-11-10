<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- <cliente :teste="clienteRodrigo"></cliente>
    <cliente :teste="clienteRodrigo"></cliente>
    <cliente :teste="clienteRodrigo" :showIdade="true"></cliente> -->
      <div v-for="(cliente, index) in clientes" :key="cliente.id">
        <h3>{{index}}</h3>
        <cliente :cliente="cliente"></cliente>
        <hr>
        <h3>Edição:</h3>
        <input type="text" v-model="cliente.nome">
        <input type="text" v-model="cliente.sobrenome">
      </div>
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
      },
      clientes: [
        {
          id: 1,
          nome: "Lorem",
          sobrenome: "Ipsum",
          idade: 26
        },
        {
          id: 2,
          nome: "Chuck",
          sobrenome: "Norris",
          idade: 146
        },
        {
          id: 3,
          nome: "Vitu",
          sobrenome: "Souza",
          idade: 52
        },
        {
          id: 4,
          nome: "Max",
          sobrenome: "Payne",
          idade: 10
        },

      ]
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
