<template>
  <div class="rounded-lg border-orange-50">
    <div class="bg-gradient-to-r from-orange-50 to-orange-400 h-16" />
    <div class="divide-y-4 divide-gray-950">
        <!-- Game screen -->
        <div class="bg-[url('/img/bgpokegame.png')] h-96 grid grid-cols-2">
            <div id="monster" class="flex flex-row">
                <div class="mt-36 ml-12 pr-5">
                  <PokemonStatus :PokemonInfos="controlledCharacter"/>
                </div>
            </div>
            <div id="ennemy" class="flex flex-row-reverse">
                <div class="mt-8">
                  <PokemonStatus :PokemonInfos="enemyCharacter"/>
                </div>
            </div>
            <div class="bg-white rounded border border-yellow-500 m-1 col-span-2">
              <FightInfos v-if="startToFight == true" :fightInfo="textFightInfo" />
              <FightInfos v-else :fightInfo="'Que dois faire '+ controlledCharacter.name +' ?'" />
            </div>
        </div>
        <!-- Game actions -->
        <div class="h-24 grid grid-cols-3 place-content-center">
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
    choosenPokemon: Object,
  },
  data() {
    return {
      controlledCharacter: { name: this.choosenPokemon.name, 
                             typeIcon: this.choosenPokemon.typeIcon, 
                             health: this.choosenPokemon.health, 
                             img: this.choosenPokemon.img,
                             colorbar: "bg-green-500" 
                            },
      enemyCharacter:       { name: "Phyllali", 
                              typeIcon: '/img/icons/plante.png', 
                              health: 73, 
                              img: '/img/phyllali.png',
                              colorbar: "bg-green-500" 
                            },
      textFightInfo : "",
      startToFight : false,
      healCount: 0, // Compteur pour limiter les soins à 3 fois
      victory: 0
    };
  },
  methods: {
    updateFightInfos(text: string) {
        this.textFightInfo = text
    },
    attack() {
      this.startToFight = true
      // Attaque du joueur sur l'ennemi
      this.attackAction(this.controlledCharacter, this.enemyCharacter)
      // Vérifier si l'ennemi est vaincu
      this.checkIfIsStillAlive(this.enemyCharacter.health, true)

      setTimeout(() => {
      // Attaque de l'ennemi sur le joueur
        this.attackAction(this.enemyCharacter, this.controlledCharacter)
      }, 3000)
      // Vérifier si le joueur est vaincu
      this.checkIfIsStillAlive(this.controlledCharacter.health, false)

      setTimeout(() => {
        this.startToFight = false
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
      // Vérifier si le joueur peut se soigner
      if (this.healCount < 3) {
        // Ajouter la logique de soin ici
        const healingAmount = Math.floor(Math.random() * 5) + 1;
        this.controlledCharacter.health += healingAmount;

        // Limiter les soins à 3 fois
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
