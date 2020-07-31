<template>
  <div>
    <poke-list :pokemons="pokemons"></poke-list>
  </div>
</template>

<script>
import { eventBus } from './main.js'
import PokeList from './components/PokeList.vue'

export default {
  data(){
    return {
      pokemons: []
    }
  },
  mounted(){
    fetch("https://pokeapi.co/api/v2/pokemon?limit=100&offset=200")
    .then(res => res.json())
    .then(pokemons => this.pokemons = pokemons.results)

    // .results.forEach(pokemon => this.pokeURL.push(pokemon.url))

    // let promise = Promise.all(this.pokeURL.map(url =>
    //   fetch(url)
    //   .then(res => res.json())).then(pokemons => this.pokemons = pokemons))
  },
  components: {
    "poke-list": PokeList
  },
  computed: {
    //  getIndex(){
    //   this.pokeURL.forEach(url => this.pokemonU.push(pokemon.url))
    }
  }
</script>

<style>

</style>