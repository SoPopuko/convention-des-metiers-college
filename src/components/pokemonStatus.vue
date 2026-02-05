<template>
    <div>
        <HealthBar :pokemon="PkmInfoStatus" :isShaymin="ShayminIsHere"/>
        <img v-if="ShayminIsHere == false" class="w-28" :src="PkmInfoStatus!.img" />
        <img v-else class="w-28" :src="PkmInfoStatus!.img" :class="{'cursor-pointer': ShayminIsHere == true}" @click="$emit('pet', 'vous avez carressé votre pokémon !')" />
    </div>
</template>

<script lang="ts">
import HealthBar from './healthBar.vue';

export default {
  components: {
    HealthBar
  },
  props: {
    PkmInfoStatus: Object,
    ShayminIsHere: Boolean
  }
};
</script>
