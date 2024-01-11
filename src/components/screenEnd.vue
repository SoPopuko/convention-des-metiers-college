<template>
    <div style="text-align: center;border:purple solid 2px">
      <h1>ICI l'écran screen WIN/LOSE</h1>
      <div v-if="victory === 1" style="padding: 10px;">
        <p>Félicitation, vous avez gagné face au monstre !</p>
        <p>Vous voulez rejoué ?</p>
        <button>Nouveau combat</button>
      </div>
      <div v-else-if="victory === 2" style="padding: 10px;">
        <p class="text-red-700">Dommage, le monstre vous a battu</p>
      </div>
    </div>
  </template>

  <script>
  export default {
    victory: {
      type: Number,
      required: true,
    },
  };
  </script>
