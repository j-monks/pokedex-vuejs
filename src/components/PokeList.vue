<template lang="html">
    <div class="row">
        <pokemon v-for="(pokemon, index) in filteredPokemon" :name="pokemon.name" :url="pokemon.url" :key="pokemon.name"></pokemon>
    </div>
</template>

<script>
import Pokemon from './Pokemon.vue'

export default {
    name: 'poke-list',
    props: ['filteredPokemon'],
    components: {
        "pokemon": Pokemon
    }
} 
</script>

<style lang="css" scoped>
  
</style>
