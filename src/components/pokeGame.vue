<template>
  <div class="rounded-lg border-orange-50">
    <div class="bg-gradient-to-r from-orange-50 to-orange-400 h-16" />
    <div class="divide-y-4 divide-gray-950">
        <!-- Game screen -->
        <div class="bg-[url('/img/bgpokegame.png')] h-96 grid grid-cols-2">
            <div id="monster" class="flex flex-row">
                <div class="mt-32 ml-12 pr-5">
                  <PokemonStatus :PkmInfoStatus="choosenPkm"/>
                </div>
            </div>
            <div id="ennemy" class="flex flex-row-reverse">
                <div class="mt-8">
                  <PokemonStatus :PkmInfoStatus="ennemyCharacter"/>
                </div>
            </div>
            <div class="bg-white rounded border border-yellow-500 m-1 col-span-2">
              <FightInfos v-if="startFightAction == true" :fightInfo="textFightInfo" />
              <FightInfos v-else :fightInfo="'Que dois faire '+ choosenPkm!.name +' ?'" />
            </div>
        </div>
        <!-- Game actions -->
        <div class="h-24 grid grid-cols-3 place-content-center" :class="{'hidden': startFightAction == true}">
            <button @click="attack" class="p-3 m-4 rounded-lg border-2 border-red-600 bg-red-800 text-neutral-950"> Compétences </button>
            <button @click="heal" :disabled="healCount >= 3" class="p-3 m-4 rounded-lg border-2 border-yellow-500 bg-yellow-700 text-neutral-950"> Se soigner ({{ 3 - healCount }})</button>
            <button @click="handleCharacterDefeated" class="p-3 m-4 rounded-lg border-2 border-orange-500 bg-orange-700 text-neutral-950"> Fuir </button>
        </div>
    </div>
    <div class="bg-gradient-to-r from-orange-50 to-orange-400 h-16" />

    <result :victory="victory" v-if="victory !==0"/>
  </div>
</template>

<script lang="ts">
import ennemyData from '../assets/ennemies.json'
import FightInfos from './fightInfos.vue';
import result from './screenEnd.vue';
import PokemonStatus from './pokemonStatus.vue';

export default {
  components: {
    result,
    FightInfos,
    PokemonStatus
  },
  props: {
    choosenPkm: Object,
  },
  data() {
    return {
      ennemyCharacter: ennemyData[0],
      textFightInfo : "",
      startFightAction : false,
      healCount: 0, // Compteur pour limiter les soins à 3 fois
      victory: 0
    };
  },
  methods: {
    updateFightInfos(text: string) {
        this.textFightInfo = text
    },
    attack() {
      this.startFightAction = true
      // Attaque du joueur sur l'ennemi
      this.attackAction(this.choosenPkm, this.ennemyCharacter)
      // Vérifier si l'ennemi est vaincu
      this.checkIfIsStillAlive(this.ennemyCharacter.health, true)

      setTimeout(() => {
      // Attaque de l'ennemi sur le joueur
        this.attackAction(this.ennemyCharacter, this.choosenPkm)
      }, 3000)
      // Vérifier si le joueur est vaincu
      this.checkIfIsStillAlive(this.choosenPkm!.health, false)

      setTimeout(() => {
        this.startFightAction = false
      }, 6000)
    },
    attackAction(fighter: any, victim: any){
      const fighterDamage = Math.floor(Math.random() * 5) + 1;
      victim.health -= fighterDamage;
      this.updateFightInfos(`${fighter.name} attaque ${victim.name} et lui inflige ${fighterDamage} dégâts.`)
    },
    checkIfIsStillAlive(characterHealth: number, isenemy: boolean){
      if (characterHealth <= 0) {
        characterHealth = 0
        if(isenemy == true){
          this.handleEnemyDefeated();
        } else {
          this.handleCharacterDefeated();
        }
      }
    },
    heal() {
      this.startFightAction = true
      // Vérifier si le joueur peut se soigner
      if (this.healCount < 3) {
        // Ajouter la logique de soin ici
        const healingAmount = Math.floor(Math.random() * 5) + 12;
        this.choosenPkm!.health += healingAmount;

        if(this.choosenPkm!.health > this.choosenPkm!.maxhealth){
          this.choosenPkm!.health = this.choosenPkm!.maxhealth
        }

        // Limiter les soins à 3 fois
        this.healCount++;
        
        this.updateFightInfos(`${this.choosenPkm!.name} se soigne de ${healingAmount} PV !`)
      }
      
      setTimeout(() => {
        this.startFightAction = false
      }, 6000)
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
