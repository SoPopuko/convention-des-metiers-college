<template>
    <div class="w-32 m-2">
      <div class="bg-white rounded p-2 cursor-pointer" :class="{ 'border border-4 border-slate-950': isSelected == true }">
        <div class="text-center"  @click="PokemonIsSelected()">
            <img class="m-2" style="height: 6rem; width: auto;" :src=imgPokemon  />
            <span class="text-indigo-900"> {{namePokemon}}</span>
        </div>
      </div>
    </div>
  </template>

<script>
export default {
  props: {
    imgPokemon: String,
    namePokemon: String,
  },

  data() {
    return {
      isSelected: true
    };
  },
  methods: {
    PokemonIsSelected() {
      isSelected == true
      $emit(['pokemonName', this.namePokemon], ['pokemonPicture', this.imgPokemon])
    }
  }
};
</script>

