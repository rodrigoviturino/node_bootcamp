<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- Cadastro -->
    <h3>Cadastro</h3>
    <p class="deuErro" v-if="deuErro">Verifique os campos para cadastrar.</p>
    <input type="text" placeholder="Nome" v-model="nomeField"><br>
    <input type="text" placeholder="Sobrenome" v-model="sobrenomeField"><br>
    <input type="number" placeholder="Idade" v-model="idadeField"><br>
    <button @click="cadastrarUsuario">Cadastrar</button>
    <!-- end Cadastro -->

    <!-- <cliente :teste="clienteRodrigo"></cliente>
    <cliente :teste="clienteRodrigo"></cliente>
    <cliente :teste="clienteRodrigo" :showIdade="true"></cliente> -->
      <div v-for="(cliente, index) in orderClientes" :key="cliente.id">
        <h3>{{index}}</h3>
        <input type="text" v-model="cliente.nome">
        <input type="text" v-model="cliente.sobrenome">
        <cliente :cliente="cliente" @deletando="deletarUsuario($event)"></cliente>
        <hr>
        <h3>Edição:</h3>
        <div class="buttons">
  <button class="button is-primary">Primary</button>
  <button class="button is-link">Link</button>
</div>
      </div>
  </div>
</template>

<script>
import _ from "lodash";
import Cliente from './components/Cliente.vue'

export default {
  name: 'App',
  components: {
    Cliente
  },
  data(){
    return {
      nomeField : "",
      sobrenomeField: "",
      idadeField: null,
      deuErro: false,
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
  methods: {
    cadastrarUsuario(){
      if(this.nomeField == "" || this.nomeField == " " || this.nomeField.length < 3){
        this.deuErro = true;
        this.deuErro = true;
      }else{
        this.clientes.push({
          nome: this.nomeField,
          sobrenome: this.sobrenomeField,
          idade: this.idadeField
        });
        this.nomeField = "";
        this.sobrenomeField = "";
        this.idadeField = "";
        this.deuErro = false;
        console.log(this.orderClientes);
      }
    },
    deletarUsuario($event){
      console.log("Recebendo evento do pai");
      let id = $event.idDoCliente;
      let deletando = this.clientes.filter(cliente => cliente.id != id)
      this.clientes = deletando;
    }
  },
  computed: {
    orderClientes(){
      return _.orderBy(this.clientes, ["nome"], ["desc"]);
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
.deuErro{
  color: darkred;
}
</style>
