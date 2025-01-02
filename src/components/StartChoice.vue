<template>
    <div class="w-auto mx-7 my-16">
      <div class="border-2 border-slate-600 bg-slate-800 text-center rounded-lg">
        <h3>
          Choisi ton pokemon !
        </h3>
        <div class="grid grid-cols-3 gap-4 content-center">
            <PokemonSelector :imgPokemon="'/img/mimiqui.png'" :namePokemon="'Mimiqui'"  />
            <PokemonSelector :imgPokemon="'/img/keunotor.png'" :namePokemon="'Keunotor'"  />
            <PokemonSelector :imgPokemon="'/img/salameche.png'" :namePokemon="'Salameche'"  />
        </div>
        <button class="w-24 p-3 m-4 rounded-lg border-2 border-green-600 bg-green-800 text-neutral-950"> Go ! </button>
      </div>
    </div>
  </template>

<script setup lang="ts">
import PokemonSelector from './PokemonSelector.vue'
</script>