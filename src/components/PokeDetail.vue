<template>
    <div class="col-md-3 col-sm-6 mb-5 mx-auto">
        <div class="card mx-auto">
            <div class="header">
                <h5 v-if="selectedPokemon" class="card-header text-center">{{upperCase(selectedPokemon.name)}}</h5>
            </div>
            <div class="card-body mx-auto">
                <h6 class="card-title">
                    Base XP: {{selectedPokemon.base_experience}}
                </h6>
                <h6 class="card-title">
                    Ability: {{upperCase(selectedPokemon.abilities[0].ability.name)}}
                </h6>
                <h6 class="card-title">
                    Type: {{upperCase(selectedPokemon.types[0].type.name)}}
                </h6>
            </div>
        </div>
    </div>
</template>
   
<script>
export default {
    created() {


        console.log(this.selectedPokemon);

    },

    name: "poke-detail",
    props: ["selectedPokemon"],

    methods: {
        upperCase(name) {
            const newName = name.toLowerCase()
                .split(" ")
                .map(letter => letter.charAt(0).toUpperCase() + letter.substring(1))
                .join(" ")

            return newName;
        }
    }

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