<template>
    <div class="p-2 text-black text-base">
        {{ fightInfo }}
    </div>
  </template>
  
  <script lang="ts">
  export default {
    props: {
      fightInfo: String,
    },
  };
  </script>