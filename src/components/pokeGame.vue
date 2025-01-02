<template>
  <div class="rounded-lg border-orange-50">
    <div class="bg-gradient-to-r from-orange-50 to-orange-400 h-16" />
    <div class="divide-y-4 divide-gray-950">
        <!-- Game screen -->
        <div class="bg-[url('/img/bgpokegame.png')] h-80 grid grid-cols-2">
            <div id="monster" class="flex flex-row">
                <div class="mt-36 ml-12 pr-5">
                    <div name="monster-bar" class="flex m-2 w-40 h-5 border-slate-950 border-4 rounded-lg">
                        <div v-for="index in controlledCharacter.health" :key="index" class="h-3 w-2 bg-green-500" />
                    </div>
                    <img class="w-32" src="/img/mimiqui.png" />
                </div>
            </div>
            <div id="ennemy" class="flex flex-row-reverse">
                <div class="mt-20">
                    <div id="ennemy-bar" class="flex m-2 w-40 h-5 border-slate-950 border-4 rounded-lg">
                        <div v-for="index in enemyCharacter.health" :key="index" class="h-3 w-2 bg-red-500" />
                    </div>
                    <img class="w-32" src="/img/phyllali.png" />
                </div>
            </div>
        </div>
        <!-- Game actions -->
        <div class="h-24 grid grid-cols-3 place-content-center">
            <button @click="attack" class="p-3 m-4 rounded-lg border-2 border-red-600 bg-red-800 text-neutral-950"> Compétences </button>
            <button @click="heal" :disabled="healCount >= 2" class="p-3 m-4 rounded-lg border-2 border-yellow-500 bg-yellow-700 text-neutral-950"> Se soigner ({{ 2 - healCount }})</button>
            <button @click="handleCharacterDefeated" class="p-3 m-4 rounded-lg border-2 border-orange-500 bg-orange-700 text-neutral-950"> Fuir </button>
        </div>
    </div>
    <div class="bg-gradient-to-r from-orange-50 to-orange-400 h-16" />

    <result :victory="victory" v-if="victory !==0"/>
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
      controlledCharacter: { name: 'Joueur', health: 20 },
      enemyCharacter: { name: 'Ennemi', health: 50 },
      healCount: 0, // Compteur pour limiter les soins à 2 fois
      victory: 0
    };
  },
  methods: {
    attack() {
      // Attaque du joueur sur l'ennemi
      const playerDamage = Math.floor(Math.random() * 5) + 1;
      this.enemyCharacter.health -= playerDamage;
      console.log(`Le joueur attaque l'ennemi et lui inflige ${playerDamage} dégâts.`);

      // Vérifier si l'ennemi est vaincu
      if (this.enemyCharacter.health <= 0) {
        this.enemyCharacter.health = 0

        this.handleEnemyDefeated();
      }

      // Attaque de l'ennemi sur le joueur
      const enemyDamage = Math.floor(Math.random() * 5) + 1;
      this.controlledCharacter.health -= enemyDamage;
      console.log(`L'ennemi contre-attaque et inflige ${enemyDamage} dégâts au joueur.`);

      // Vérifier si le joueur est vaincu
      if (this.controlledCharacter.health <= 0) {
        this.controlledCharacter.health = 0
        this.handleCharacterDefeated();
      }
    },
    heal() {
      // Vérifier si le joueur peut se soigner
      if (this.healCount < 2) {
        // Ajouter la logique de soin ici
        const healingAmount = Math.floor(Math.random() * 5) + 1;
        this.controlledCharacter.health += healingAmount;

        // Limiter les soins à 2 fois
        this.healCount++;

        console.log(`Le joueur se soigne de ${healingAmount} points de vie.`);
      }
    },
    handleCharacterDefeated() {
      console.log('Le joueur a été vaincu!');
      this.victory = 2; // Défaite
    },
    handleEnemyDefeated() {
      console.log('L\'ennemi a été vaincu!');
      this.victory = 1; // Victoire
    },
  },

};
</script>
