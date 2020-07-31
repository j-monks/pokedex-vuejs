<template lang="html">
  <div id="pokeList">
    <ul>
      <list-item  v-for="(pokemon, index) in pokemons" :pokemon="pokemon" :key="index"></list-item>
    </ul>
  </div>

</template>

<script>
import ListItem from './ListItem.vue'
export default {
  name: 'poke-list',
  props: ['pokemons'],
  components: {
    "list-item": ListItem
  }
}
</script>

<style lang="css" scoped>
  #countriesList {
    background: #eee;
    height: 400px;
    overflow-y: scroll;
    border: 1px solid #ccc;
  }

  #countriesList ul {
    margin: 10px;
    padding: 0;
  }

  ::-webkit-scrollbar {
    -webkit-appearance: none;
    width: 7px;
  }

  ::-webkit-scrollbar-thumb {
    border-radius: 4px;
    background-color: rgba(0,0,0,.5);
    -webkit-box-shadow: 0 0 1px rgba(255,255,255,.5);
  }
</style>
