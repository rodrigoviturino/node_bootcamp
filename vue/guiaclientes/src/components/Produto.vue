<template>
  <div>
    <input type="text" v-model="nome">
    <input type="text" :value="sobrenome">
    <br>
    {{nome}} | {{sobrenome}}
  </div>
</template>

<script>
export default {
  name: "Produto",
  data(){
    return{
      nome: "Rodrigo",
      sobrenome: "Viturino",
      idade: 0,
      faculdade: true
    }
  },

}
</script>

<style scoped>

</style>