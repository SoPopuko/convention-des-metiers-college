<template>
  <div class="rounded-lg border-orange-50">
    <div class="bg-gradient-to-r from-orange-50 to-orange-400 h-16" />
    <div class="divide-y-4 divide-gray-950">
        <!-- Game screen -->
        <div class="bg-[url('/img/bgpokegame.png')] h-80 grid grid-cols-2">
            <div id="monster" class="flex flex-row">
                <div class="mt-36 ml-12 pr-5">
                    <div id="monster-bar" class="m-2 w-40 h-5 border-slate-950 border-4 rounded-xl"> </div>
                    <img class="w-32" src="/img/mimiqui.png" />
                </div>
            </div>
            <div id="ennemy" class="flex flex-row-reverse">
                <div class="mt-20">
                    <div id="ennemy-bar" class="m-2 w-40 h-5 border-slate-950 border-4 rounded-xl"> </div>
                    <img class="w-32" src="/img/phyllali.png" />
                </div>
            </div>
        </div>
        <!-- Game actions -->
        <div class="h-24 grid grid-cols-3 place-content-center border-top-red-600">
            <button class="p-3 m-4 rounded-lg border-2 border-red-600 bg-red-800 text-neutral-950"> Attaquer </button>
            <button class="p-3 m-4 rounded-lg border-2 border-yellow-500 bg-yellow-700 text-neutral-950"> Ouvrir le sac </button>
            <button class="p-3 m-4 rounded-lg border-2 border-orange-500 bg-orange-700 text-neutral-950"> Fuir </button>
        </div>
    </div>
    <result :isWin="False"/>
    <div class="bg-gradient-to-r from-orange-50 to-orange-400 h-16" />
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
