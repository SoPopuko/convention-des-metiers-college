<template>
    <div class="w-32 m-2">
      <div class="bg-white rounded p-2">
        <div class="text-center">
            <img class="m-2" style="height: 6rem; width: auto;" :src=imgPokemon  />
            <span class="text-indigo-900"> {{namePokemon}}</span>
        </div>
      </div>
    </div>
  </template>

<script>
export default {
  props: {
    imgPokemon: String,
    namePokemon: String,
  },
};
</script>

