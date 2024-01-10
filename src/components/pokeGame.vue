<template>
  <div style="border: 2px solid yellow; padding: 10px; margin-top: 50px">
    <div style="border: 2px solid white; height:300px">

        <div id="monster" style="padding: 10px; border: 2px solid orange">
            <div id="monster-bar" style="border: 2px solid green; height:25px; width:150px"> </div>
            <img style="border: 2px solid red; width: 130px; float: left; margin: 20px; margin-top: 90px" src="/public/img/mimiqui.png" />
        </div>
        <div id="ennemy" style="padding: 10px; border: 2px solid skyblue">
            <div id="ennemy-bar" style="border: 2px solid red; height:25px; width:150px"> </div>
            <img style="border: 2px solid green; width: 110px; float: right; margin: 20px" src="/public/img/phyllali.png" />
        </div>


    </div>
    <div style="border: 2px solid orange; height:100px">
        <button> Attaquer </button>
        <button> Ouvrir le sac </button>
        <button> Fuir </button>
    </div>
    <result :isWin="False"/>
  </div>
</template>

<script>
import result from './screenEnd.vue';

export default {
  components: {
    result,
  },
  data() {
    return {
      False: false,
      True: true,
    };
  },
};
</script>
