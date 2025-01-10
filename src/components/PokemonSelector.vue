<template>
    <div class="w-32 m-2">
      <div class="bg-white rounded p-2 cursor-pointer">
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
      pokemonName: ""
    };
  },
  methods: {
    PokemonIsSelected() {
      this.pokemonName = this.namePokemon!

      this.$emit('updatepoke', this.pokemonName)
    }
  }
};
</script>

