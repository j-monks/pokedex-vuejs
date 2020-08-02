<template>
    <div>
        <nav class="navbar navbar-expand-md navbar-dark bg-dark fixed-top">
            <a class="navbar-brand" href="#">Pokedex</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>

            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <div class="mx-auto">
                    <form class="form-inline">
                        <input class="form-control mr-sm-2" v-model="search" id="navBarSearchInput" type="search" placeholder="Search" aria-label="Search" />
                    </form>
                </div>
            </div>
        </nav>
        <div class="container">
            <poke-detail :selectedPokemon="pokemonDetails"></poke-detail>
            <div class="row">
                <div class="col">
                    <poke-list :filteredPokemon="filteredPokemon"></poke-list>
                </div>
            </div>
        </div>
    </div>
</template>


<script>
import { eventBus } from './main.js'
import "bootstrap/dist/css/bootstrap.min.css"
import PokeList from './components/PokeList.vue'
import PokeDetail from "./components/PokeDetail.vue"

export default {
    data() {
        return {
            pokemons: [],
            selectedPokemon: null,
            pokemonDetails: [],
            search: ""
        }
    },
    mounted() {
        fetch("https://pokeapi.co/api/v2/pokemon?limit=100&offset=0")
            .then(res => res.json())
            .then(pokemons => this.pokemons = pokemons.results),

            eventBus.$on('pokemon-selected', (selectedPokemon) => {
                this.selectedPokemon = selectedPokemon;
            }),

            eventBus.$on('pokemon-details', (details) => {
                this.pokemonDetails = details;
            }),

            fetch(selectedPokemon)
            .then(res => res.json())
            .then(details => this.pokemonDetails = details)
    },
    components: {
        "poke-list": PokeList,
        "poke-detail": PokeDetail
    },
    computed: {
        filteredPokemon: function() {
            return this.pokemons.filter((pokemon) => {
                return pokemon.name.match(this.search);
            })
        }
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