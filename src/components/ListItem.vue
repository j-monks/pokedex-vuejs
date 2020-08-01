<template lang="html">
<div class="pokemon">
      <h3 v-on:click="handleClick">{{name}}</h3>
      <img class="img" :src="imageUrl"></img>
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

</style>
