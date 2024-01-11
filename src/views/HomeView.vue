<template>
  <div class="flex text-xl">
    <FAQ class="w-4/12 mr-4" />
    <PokeGame class="w-4/12 m-auto bg-white" />
    <VF class="w-4/12 ml-4" />
  </div>
</template>


<script setup lang="ts">
  import FAQ from '../components/faq.vue'
  import VF from '../components/faq-vf.vue'
  import PokeGame from '../components/pokeGame.vue'
</script>
