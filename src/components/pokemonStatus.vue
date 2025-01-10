<template>
    <div>
        <HealthBar :pokemon="PkmInfoStatus"/>
        <img class="w-32" :src="PkmInfoStatus!.img" />
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
  }
};
</script>
