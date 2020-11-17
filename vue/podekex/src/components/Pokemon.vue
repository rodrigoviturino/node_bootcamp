<template>
  <div class="card" id="pokemon">
    <div class="card-image">
      <figure>
        <img :src="currentImg" alt="Placeholder image" />
      </figure>
    </div>
    <div class="card-content">
      <div class="media">
        <div class="media-content">
          <p class="title is-4">{{ num }} {{ name | upper }}</p>
          <p class="subtitle is-6">{{ dadosAPI.type }}</p>
          <button class="button is-link is-rounded" @click="clickImgFront">
            Alterar Imagem
          </button>
        </div>
      </div>

      <div class="content"></div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Pokemon",
  data() {
    return {
      dadosAPI: {
        type: "",
        front: "",
        back: "",
      },
      currentImg: "",
      imgFront: true,
    };
  },
  methods: {
    clickImgFront() {
      if (this.imgFront) {
        this.imgFront = false;
        this.currentImg = this.dadosAPI.back;
      } else {
        this.imgFront = true;
        this.currentImg = this.dadosAPI.front;
      }
    },
  },
  created() {
    axios.get(this.url).then((response) => {
      this.dadosAPI.type = response.data.types[0].type.name;
      this.dadosAPI.front = response.data.sprites.front_default;
      this.dadosAPI.back = response.data.sprites.back_default;
      this.currentImg = response.data.sprites.front_default;
      console.log(this.dadosAPI);
    });
  },
  props: {
    num: Number,
    name: String,
    url: String,
  },
  filters: {
    upper(value) {
      return value.charAt(0).toUpperCase() + value.slice(1);
    },
  },
};
</script>

<style>
#pokemon {
  margin-top: 2rem;
}
</style>
