<template>
    <div class="w-32 m-2">
      <div class="bg-white rounded p-2 cursor-pointer" :class="{'border border-4 border-green-800': isSelected == true, 'border-0': isSelected == false }">
        <div class="text-center"  @click="PokemonIsSelected()">
            <img class="m-2" style="height: 6rem; width: auto;" :src=imgPokemon  />
            <span class="text-indigo-900"> {{namePokemon}}</span>
        </div>
      </div>
    </div>
  </template>

<script lang="ts">
export default {
  props: {
    imgPokemon: String,
    namePokemon: String,
  },
  data() {
    return {
      isSelected: false,
      pokemonInfo: {}
    };
  },
  methods: {
    PokemonIsSelected() {
      if (this.isSelected == true){
        this.isSelected = false
      }
      this.isSelected = true
      this.pokemonInfo = { name: this.namePokemon, img: this.imgPokemon }
      
      console.log(this.pokemonInfo)

      this.$emit('updatepoke', this.pokemonInfo)
    }
  }
};
</script>

