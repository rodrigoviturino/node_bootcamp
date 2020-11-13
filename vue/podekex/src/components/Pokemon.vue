<template>
  <div>
      <h1>{{num}} {{name | upper}}</h1>
      <small>{{url}}</small>
  </div>
</template>

<script>
export default {
    name: "Pokemon",
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