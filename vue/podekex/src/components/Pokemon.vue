<template>
  <div>
      <h1>{{num}} {{name | upper}}</h1>
      <small>{{url}}</small>
  </div>
</template>

<script>
import axios from "axios";

export default {
    name: "Pokemon",
    data(){
        return {
            dadosAPI: {}
        }
    },
    created(){
        axios.get(this.url).then((response) => {
            this.dadosAPI.type = response.data.types[0].type.name;
            this.dadosAPI.front = response.data.sprites.front_default;
            this.dadosAPI.front = response.data.sprites.back_default;
            console.log(this.dadosAPI);
        })

    },
    props: {
        num: Number,
        name: String,
        url: String,
    },
    filters: {
        upper(value){
            return value.charAt(0).toUpperCase() + value.slice(1)
        }
    }
}
</script>

<style>

</style>