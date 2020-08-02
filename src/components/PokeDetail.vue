<template>
 <div class="col-md-3 col-sm-6 mb-5 mx-auto">
  <div class="card">
    <h5 class="card-header">Selected-Pokemon</h5>
    <div class="card-body mx-auto">
      <h6 class="card-title">
        {{selectedPokemon}}
      </h6>
    </div>
  </div>
</div>   
</template>
   
<script>


export default {
   name: "poke-detail",
   props: ["selectedPokemon"] 
}
</script>

<style>
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