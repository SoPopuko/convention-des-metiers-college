<template>
    <div style="text-align: center;border:purple solid 2px">
      <h1>ICI l'écran screen WIN/LOSE</h1>
      <div style="padding: 10px;" v-if="isWin">
        <p>Félicitation, vous avez gagné face au monstre !</p>
        <p>Vous voulez rejoué ?</p>
        <button>Nouveau combat</button>
      </div>
      <div style="padding: 10px;" v-else>
        <p>Dommage, le monstre vous a battu</p>
        <p>Vous voulez retenté ?</p>
        <button>Nouveau combat</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      isWin: Boolean,
    },
  };
  </script>