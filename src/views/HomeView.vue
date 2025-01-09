<template>
  <div class="flex text-xl relative ">
     <FAQ class="w-4/12 mr-4" />
     <StartChoice @submitpoke="GetChoosen" class="absolute" :class="{'hidden': isChoosen == true}" />
     <PokeGame :choosenPokemon="choosenPokemonInfos" :class="{'hidden': isChoosen == false}" />
     <VF class="w-4/12 ml-4" />
  </div>
</template>


<script lang="ts">
  import FAQ from '../components/faq.vue'
  import VF from '../components/faq-vf.vue'
  import PokeGame from '../components/pokeGame.vue'
  import StartChoice from '../components/StartChoice.vue'

  export default {
  components: {
    StartChoice,
    PokeGame,
  },
  data() {
    return {
      choosenPokemonInfos: { name: "Mimiqui", img: "/img/phyllali.png" },
      isChoosen: false
    };
  },
  methods: {
    GetChoosen(pokemonInfos: any){
      this.choosenPokemonInfos = pokemonInfos
      this.isChoosen = true
      console.log(this.choosenPokemonInfos)
    }
  }
};
</script>
