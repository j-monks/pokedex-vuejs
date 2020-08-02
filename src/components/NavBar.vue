<template>
    <nav class="navbar navbar-expand-md navbar-dark bg-dark fixed-top">
  <a class="navbar-brand" href="#">Pokedex</a>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>

  <div class="collapse navbar-collapse" id="navbarSupportedContent">
    <div class="mx-auto">
    <form class="form-inline">
        <input class="form-control mr-sm-2" v-model="search" id="navBarSearchInput" type="search" placeholder="Search" aria-label="Search">
    </form>
    </div>
  </div>
</nav>
</template>

<script>
import { eventBus } from '../main.js'
export default {
    data() {
        return {
            search: "hello"
        }
    },
    mounted(){
        emitGlobalEvent();
    },
    methods: {
       emitGlobalEvent() {
          return  eventBus.$emit('search-term', this.search)
       }    
    }
}
</script>

<style>
   /* <nav class="navbar navbar-expand-md navbar-dark bg-dark fixed-top">
         <a class="navbar-brand col-sm-3 col-md-2 mr-0 align-items-center">Pokedex</a>
         <form class="form-inline">
             <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
             <button class="btn btn-warning my-2 my-sm-0" type="submit">Search</button>
         </form>
     </nav> */
</style>

