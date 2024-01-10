<template>
  <div style="padding: 10px">
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