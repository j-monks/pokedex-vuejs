<template>
  <div>
    <nav-bar></nav-bar>
    <div class="container">
      <div class="row">
        <div class="col">
          <poke-list :pokemons="pokemons"></poke-list>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { eventBus } from './main.js'
import "bootstrap/dist/css/bootstrap.min.css"
import PokeList from './components/PokeList.vue'
import NavBar from "./components/NavBar.vue"

export default {
  data(){
    return {
      pokemons: []
    }
  },
  mounted(){
    fetch("https://pokeapi.co/api/v2/pokemon?limit=100&offset=0")
    .then(res => res.json())
    .then(pokemons => this.pokemons = pokemons.results)

    // .results.forEach(pokemon => this.pokeURL.push(pokemon.url))

    // let promise = Promise.all(this.pokeURL.map(url =>
    //   fetch(url)
    //   .then(res => res.json())).then(pokemons => this.pokemons = pokemons))
  },
  components: {
    "poke-list": PokeList, 
    "nav-bar": NavBar
  },
  computed: { 
    //  getIndex(){ 
    //   this.pokeURL.forEach(url => this.pokemonU.push(pokemon.url))
    }
  }
</script>

<style>
  .container {
    padding-top: 5rem;
    min-height: 100vh;
  }

  .navbar {
        background-color: #ef5450 !important;
    }

   #navBarSearchInput {
        width: 430px;
    }

</style>