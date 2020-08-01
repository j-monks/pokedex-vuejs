<template lang="html">
<div class="col-md-3 col-sm-6 mb-5">
  <div class="card">
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
      imageUrl: null
    }
  },

  computed: {
    
  },

  mounted(){
    this.getIndex();
    this.getUrl();
  },
  
  methods: {
    handleClick(){
      eventBus.$emit('pokemon-selected', this.pokemon)
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
</style>
