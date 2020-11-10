<template>
  <div>
    <h3>Nome: {{cliente.nome}}</h3>
    <p>Sobrenome: {{cliente.sobrenome}}</p>
    <p v-if="showIdade"><b>Idade</b>: {{cliente.idade}}</p>
    <p v-else><b>Idade</b>: Usuário ocultou sua idade.</p>
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
  }
}
</script>

<style scoped>
  h1 {
    font-size: 30px;
  }
</style>