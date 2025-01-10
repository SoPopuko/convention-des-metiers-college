<template>
    <div class="w-auto mx-7 my-16">
      <div class="border-2 border-slate-600 bg-slate-800 text-center rounded-lg">
        <h3>
          Choisi ton pokemon !
        </h3>
        <div  class="grid grid-cols-3 gap-4 content-center">
            <PokemonSelector v-for="pokemon in pokemons" @updatepoke="UpdatePokemonInfos" :imgPokemon="pokemon.img" :namePokemon="pokemon.name"  />
        </div>
        <h3 :class="{'hidden': selectedPokemon == null}">
          Tu as choisi : {{ selectedPokemon }}
        </h3>
        <button class="w-24 p-3 m-4 rounded-lg border-2 border-green-600 bg-green-800 text-neutral-950" @click="SendPokemonSelected()"> Go ! </button>
      </div>
    </div>
  </template>

<script lang="ts">
import PokemonSelector from './PokemonSelector.vue'
import pokemonData from '../assets/pokemons.json'

export default {
  components: {
    PokemonSelector,
  },
  data() {
    return {
      pokemons: pokemonData,
      pokemonInfos: [],
      selectedPokemon: null
    };
  },
  methods: {
    UpdatePokemonInfos(pokemonName: string){
      this.pokemons.forEach((pokemon) => {
        if(pokemon.name == pokemonName){
          this.pokemonInfos = pokemon
          this.selectedPokemon = pokemon.name
        }
      })
    },
    SendPokemonSelected() {
      this.$emit('submitpoke', this.pokemonInfos)
    }
  }
};
</script>