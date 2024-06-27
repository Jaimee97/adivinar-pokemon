<template>
  <div class="container">
    <img :src="datosPokemon.imagen" alt="imagen pokemon" :class="{
        modoFiltro: filter
    }"/>
    <div v-if="filter" class="container-inputs">
        <input type="text" id="pokemon" v-model="nombrePokemon" @keyup.enter="verificarRespuesta" />
        <button class="btn btn-warning" @click="verificarRespuesta" @submit.prevent>Descubrir <i class="fa-solid fa-magnifying-glass" style="color: #000000;"></i></button>
    </div>
    <p v-else>{{ name }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "PokemonComponent",
  props: ["name", "url"],
  data() {
    return {
      nombrePokemon: "",
      pokemon: null,
      filter: true,
    };
  },

  methods: {
    verificarRespuesta(){
        if(this.nombrePokemon == this.name){
            this.filter = false;
            const valor = 1;
            this.$emit('datos-contador', valor)
        }else{
            this.nombrePokemon = "";
        }
    }
  },

  async mounted(){
    const enlace = this.url
    const response = await axios.get(enlace)
    this.pokemon = response.data
  },

  computed: {
    datosPokemon(){
        return {
            imagen: this.pokemon?.sprites.front_default,
        }
    }
  }

};
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Tiny5&display=swap');
    .container{
        display: flex;
        flex-direction: column;
        width: 70%;
        margin: 10px auto;
    }

    .container-inputs{
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    input{
        margin-bottom: 10px;
        width: 80%;
        border-radius: 5px;
    }

    button{
        width: 80%;
        font-family: "Tiny5", sans-serif;
        font-weight: 400;
        font-style: normal;
        text-align: center;

    }

    p{
        text-align: center;
        background-color: white;
        font-family: "Tiny5", sans-serif;
        font-size: 1.5rem;
        font-weight: 400;
        font-style: normal;
    }

    .modoFiltro{
        filter: blur(5px) grayscale(100%);
    }

</style>
