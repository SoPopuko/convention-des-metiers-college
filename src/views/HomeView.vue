<template>
  <div class="flex text-xl relative ">
    <!-- <FAQ class="w-4/12 mr-4" /> -->
     <StartChoice class="absolute" /> <!-- if go is clicked -> display none-->
     <PokeGame  />
     <!-- <VF class="w-4/12 ml-4" />   class="w-4/12 m-auto bg-white"-->
  </div>
</template>


<script setup lang="ts">
 // import FAQ from '../components/faq.vue'
 // import VF from '../components/faq-vf.vue'
  import PokeGame from '../components/pokeGame.vue'
  import StartChoice from '../components/StartChoice.vue'
</script>
