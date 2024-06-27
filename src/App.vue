<template>
  <div id="app" class="container-fluid">
    <HeaderPokemon :aciertos="contador" />
    <div class="row contenedor-componentes mt-4">
      <div class="box col-12 col-lg-3 col-md-4 col-sm-6" v-for="(pokemon, index) in listaPokemones" :key="index">
        <PokemonComponent :url="pokemon.url" :name="pokemon.name" @datos-contador="recibirDatos" />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import HeaderPokemon from "./components/HeaderPokemon.vue";
import PokemonComponent from "./components/PokemonComponent.vue";

export default {
  name: 'App',
  components: {
    HeaderPokemon,
    PokemonComponent,
  },
  data(){
    return {
      listaPokemones: [],
      contador: 0,
    }
  },

  methods: {
    recibirDatos(valor){
      this.contador += valor;
    }
  },

  async mounted(){
    const url = "https://pokeapi.co/api/v2/pokemon";
    const response = await axios.get(url);
    this.listaPokemones = response.data.results
  }

}
</script>

<style scoped>
  #app{
    background-color: #ffffff;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='1587' height='264.5' viewBox='0 0 600 100'%3E%3Cg stroke='%23FFF' stroke-width='0' stroke-miterlimit='10' %3E%3Ccircle fill='%23037B79' cx='0' cy='0' r='50'/%3E%3Ccircle fill='%2392DEBA' cx='100' cy='0' r='50'/%3E%3Ccircle fill='%23FFFFD8' cx='200' cy='0' r='50'/%3E%3Ccircle fill='%23CAF2FF' cx='300' cy='0' r='50'/%3E%3Ccircle fill='%236FCCFF' cx='400' cy='0' r='50'/%3E%3Ccircle fill='%23006EB4' cx='500' cy='0' r='50'/%3E%3Ccircle fill='%23037B79' cx='600' cy='0' r='50'/%3E%3Ccircle cx='-50' cy='50' r='50'/%3E%3Ccircle fill='%2353ac9a' cx='50' cy='50' r='50'/%3E%3Ccircle fill='%23ceefc1' cx='150' cy='50' r='50'/%3E%3Ccircle fill='%23ffffff' cx='250' cy='50' r='50'/%3E%3Ccircle fill='%239de0fe' cx='350' cy='50' r='50'/%3E%3Ccircle fill='%233e9cda' cx='450' cy='50' r='50'/%3E%3Ccircle fill='%2300789c' cx='550' cy='50' r='50'/%3E%3Ccircle cx='650' cy='50' r='50'/%3E%3Ccircle fill='%23037B79' cx='0' cy='100' r='50'/%3E%3Ccircle fill='%2392DEBA' cx='100' cy='100' r='50'/%3E%3Ccircle fill='%23FFFFD8' cx='200' cy='100' r='50'/%3E%3Ccircle fill='%23CAF2FF' cx='300' cy='100' r='50'/%3E%3Ccircle fill='%236FCCFF' cx='400' cy='100' r='50'/%3E%3Ccircle fill='%23006EB4' cx='500' cy='100' r='50'/%3E%3Ccircle fill='%23037B79' cx='600' cy='100' r='50'/%3E%3Ccircle cx='50' cy='150' r='50'/%3E%3Ccircle cx='150' cy='150' r='50'/%3E%3Ccircle cx='250' cy='150' r='50'/%3E%3Ccircle cx='350' cy='150' r='50'/%3E%3Ccircle cx='450' cy='150' r='50'/%3E%3Ccircle cx='550' cy='150' r='50'/%3E%3C/g%3E%3C/svg%3E");
  }

</style>

