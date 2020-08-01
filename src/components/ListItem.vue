<template lang="html">
<div>
  <li v-on:click="handleClick">{{name}}</li>
  <img :src="imageUrl" />
</div>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  created() {
    console.log(this.url)  //"https://pokeapi.co/api/v2/pokemon/201/";
  },
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
  li {
    list-style-type: none;
    display: block;
    background: #fff;
    font-size: 16px;
    margin: 10px 0;
    padding: 10px;
    cursor: pointer;
    color: #555;
    transition: 0.1s all ease-in;
    border-radius: 3px;
  }

  li:hover {
    background: #dbe8ff;
    color: #222;
  }
</style>
