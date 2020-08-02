<template lang="html">
<div class="col-md-3 col-sm-6 mb-5">
  <div v-on:click="handleClick" class="card">
    <h5 class="card-header">{{pokeIndex}}</h5>
    <img class="card-img-top rounded mx-auto mt-2" :src="imageUrl"></img>
    <!-- <h3 v-on:click="handleClick">{{name}}</h3> -->
    <div class="card-body mx-auto">
      <h6 class="card-title">
        {{name
          .toLowerCase()
          .split(" ")
          .map(letter => letter.charAt(0).toUpperCase() + letter.substring(1))
          .join(" ")}}
      </h6>
    </div>
  </div>
</div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  // created() {
  //   console.log(this.url)  //"https://pokeapi.co/api/v2/pokemon/201/";
  // },
  name: 'list-item',
  props: ["name", "url"],
  

   data(){
    return {
      pokeIndex: [],
      imageUrl: null,
      pokemonDetails: []
    }
  },

  computed: {
    
  },

  mounted(){
    this.getIndex();
    this.getUrl();
    this.handleClick();
  },
  
  methods: {
    handleClick(){
      fetch(this.url)
        .then(res => res.json())
        .then(details => this.pokemonDetails = details)
      eventBus.$emit('pokemon-selected', this.url)
      eventBus.$emit("pokemon-details", this.pokemonDetails)
    },
    getIndex() {
     return this.pokeIndex = this.url.split("/")[6]
    },
    getUrl() {
      return this.imageUrl = `https://github.com/PokeAPI/sprites/blob/master/sprites/pokemon/${this.pokeIndex}.png?raw=true`
    }
  }
}
</script>

<style lang="css" scoped>
  img {
    width: 5em;
    height: 5em;
  }

  .card {
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
    transition: all 0.3s cubic-bezier(0.25, 0.8, 0.25, 1);
    -moz-user-select: none;
    user-select: none;
    -o-user-select: none;
  }

  .card:hover {
      box-shadow: 0 14px 28px rgba(0, 0, 0, 0.25), 0 10px 10px rgba(0, 0, 0, 0.22);
    }
</style>
