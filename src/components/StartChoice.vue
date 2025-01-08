<template>
    <div class="w-auto mx-7 my-16">
      <div class="border-2 border-slate-600 bg-slate-800 text-center rounded-lg">
        <h3>
          Choisi ton pokemon !
        </h3>
        <div class="grid grid-cols-3 gap-4 content-center">
            <PokemonSelector v-model="pokemonInfos" :imgPokemon="'/img/mimiqui.png'" :namePokemon="'Mimiqui'"  />
            <PokemonSelector v-model="pokemonInfos" :imgPokemon="'/img/keunotor.png'" :namePokemon="'Keunotor'"  />
            <PokemonSelector @updatepoke="UpdatePokemonInfos" :imgPokemon="'/img/salameche.png'" :namePokemon="'Salameche'"  />
        </div>
        <button class="w-24 p-3 m-4 rounded-lg border-2 border-green-600 bg-green-800 text-neutral-950" @click="PokemonSelected()"> Go ! </button>
      </div>
    </div>
  </template>

<script lang="ts">
import PokemonSelector from './PokemonSelector.vue'

export default {
  components: {
    PokemonSelector,
  },
  data() {
    return {
      pokemonInfos: ['Mimiqui', '/img/mimiqui.png']
    };
  },
  methods: {
    UpdatePokemonInfos(pokemonInfos: string[]){
      this.pokemonInfos = []
      this.pokemonInfos = pokemonInfos
    },
    PokemonSelected() {
      console.log(this.pokemonInfos)

      this.$emit('submitpoke', this.pokemonInfos)
    }
  }
};
</script>