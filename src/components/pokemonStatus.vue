<template>
    <div>
        <HealthBar :pokemonName="PokemonInfos.name" :typeIcon="PokemonInfos.typeIcon" :healthPoints="PokemonInfos.health" :barColor="PokemonInfos.colorbar"/>
        <img class="w-32" :src="PokemonInfos.img" />
    </div>
</template>

<script>
import HealthBar from './healthBar.vue';

export default {
  components: {
    HealthBar
  },
  props: {
    PokemonInfos: Object,
  }
};
</script>
