<template>
  <div class="flex text-xl relative ">
    <!-- <FAQ class="w-4/12 mr-4" /> -->
     <StartChoice @submitpoke="GetChoosen" class="absolute" :class="{'hidden': isChoosen == true}" /> <!-- if go is clicked -> display none-->
     <PokeGame :choosenPokemon="choosenPokemonInfos" />
     <!-- <VF class="w-4/12 ml-4" />   class="w-4/12 m-auto bg-white"-->
  </div>
</template>


<script lang="ts">
 // import FAQ from '../components/faq.vue'
 // import VF from '../components/faq-vf.vue'
  import PokeGame from '../components/pokeGame.vue'
  import StartChoice from '../components/StartChoice.vue'

  export default {
  components: {
    StartChoice,
    PokeGame,
  },
  data() {
    return {
      choosenPokemonInfos: [],
      isChoosen: false
    };
  },
  methods: {
    GetChoosen(pokemonInfos: string[]){
      this.choosenPokemonInfos = pokemonInfos
      this.isChoosen = true
      console.log("choosen pokemon infos")
      console.log(this.choosenPokemonInfos)
    }
  }
};
</script>
