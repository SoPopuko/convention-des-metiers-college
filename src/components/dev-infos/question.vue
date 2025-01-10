<template>
  <div :class="{'border-red-400 bg-red-600': !isTrue, 'border-green-600 bg-green-800': isTrue }" class="border-2 text-zinc-950">
    <div v-if="isTrue" class="text-center"> VRAI </div>
    <div v-else class="text-center"> FAUX </div>
  </div>
</template>

<script>
export default {
  props: {
    isTrue: Boolean,
  },
};
</script>
