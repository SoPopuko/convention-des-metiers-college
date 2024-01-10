<template>
  <div :class="{'border-red-400 bg-red-600': !isTrue, 'border-green-600 bg-green-800': isTrue }" class="p-2 m-4 h-12 w-18 rounded-lg border-2 text-zinc-950">
    <p v-if="isTrue">VRAI</p>
    <p v-else>FAUX</p>
  </div>
</template>

<script>
export default {
  props: {
    isTrue: Boolean,
  },
};
</script>
