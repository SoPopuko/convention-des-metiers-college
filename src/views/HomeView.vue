<template>
  <div class="flex text-xl ">
     <FAQ class="w-4/12 mr-4" />
     <StartChoice @submitpoke="GetChoosen" :class="{'hidden': startChoiceClose == true}" />
     <PokeGame :choosenPkm="choosenPkmInfos" :class="{'hidden': startChoiceClose == false}" />
     <VF class="w-4/12 ml-4" />
  </div>
</template>


<script lang="ts">
  import FAQ from '../components/dev-infos/faq.vue'
  import VF from '../components/dev-infos/faq-vf.vue'
  import PokeGame from '../components/pokeGame.vue'
  import StartChoice from '../components/StartChoice.vue'

  export default {
  components: {
    StartChoice,
    PokeGame,
    FAQ,
    VF
  },
  data() {
    return {
      choosenPkmInfos: Object,
      startChoiceClose: false
    };
  },
  methods: {
    GetChoosen(pokemonInfos: any){
      this.choosenPkmInfos = pokemonInfos
      this.startChoiceClose = true

    }
  }
};
</script>
