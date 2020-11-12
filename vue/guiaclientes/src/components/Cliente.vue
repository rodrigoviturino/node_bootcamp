<template>
  <div>
    <h3>Nome: {{cliente.nome}}</h3>
    <p>Sobrenome: {{cliente.sobrenome}}</p>
    <p v-if="showIdade"><b>Idade</b>: {{cliente.idade}}</p>
    <p v-else><b>Idade</b>: Usuário ocultou sua idade.</p>
    <button @click="eventoFilho">Deletar</button>
  </div>
</template>

<script>
export default {
  name: "Cliente",
  data(){
    return {
      cep: "12312",
    }
  },
  props: {
    texto: String,
    numero: Number,
    teste: Object,
    showIdade: Boolean,
    cliente: Object
  },
  methods: {
    eventoFilho(){
      console.log("Filho Chorando");
      this.$emit("deletando",{idDoCliente: this.cliente.id, component: this});
    }
  },

}
</script>

<style scoped>
  h1 {
    font-size: 30px;
  }
</style>