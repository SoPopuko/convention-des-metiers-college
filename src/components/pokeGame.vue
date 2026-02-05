<template>
  <div class="rounded-lg border-orange-50" >
    <div class="bg-gradient-to-r from-orange-50 to-orange-400 h-16" />
    <div class="divide-y-4 divide-gray-950">
        <!-- Game screen -->
        <div class="bg-[url('/img/bgpokegame.png')] h-96 grid grid-cols-2">
          <SkillsPopup @sendChoosenSkill="attack" :pkmSkills="choosenPkm!.attacks" class="absolute" :class="{'hidden': openActionPopup == false}"/>
          <!-- Pokemon status -->
            <div id="monster" class="flex flex-row">
                <div class="mt-32 ml-12 pr-5">
                  <PokemonStatus :PkmInfoStatus="choosenPkm" :ShayminIsHere="shayminIsHere" @pet="LetsBeatShaymin" />
                </div>
            </div>
            <div id="ennemy" class="flex flex-row-reverse">
                <div class="mt-8" :class="{'mt-20': shayminIsHere == true}">
                  <PokemonStatus :PkmInfoStatus="ennemyCharacter" :ShayminIsHere="shayminIsHere"/>
                </div>
                <img src="/public/img/gracidee.png" class="w-12 h-12 cursor-pointer" :hidden="shayminIsHere == true" @click="LegendaryAppear()" />
            </div>
            <!-- Infos text -->
            <div class="bg-white rounded border border-yellow-500 m-1 col-span-2">
              <FightInfos v-if="startFightAction == true" :fightInfo="textFightInfo" />
              <FightInfos v-else :fightInfo="'Que dois faire '+ choosenPkm!.name +' ?'" />
            </div>
        </div>
        <!-- Game actions -->
        <div class="h-24 grid grid-cols-3 place-content-center" :class="{'hidden': startFightAction == true}">
            <button @click="openActionPopup = true" class="p-3 m-4 rounded-lg border-2 border-red-600 bg-red-800 text-neutral-950"> Compétences </button>
            <button @click="heal()" :disabled="healCount >= 3" class="p-3 m-4 rounded-lg border-2 border-yellow-500 bg-yellow-700 text-neutral-950"> Se soigner ({{ 3 - healCount }})</button>
            <button @click="handleCharacterDefeated()" class="p-3 m-4 rounded-lg border-2 border-orange-500 bg-orange-700 text-neutral-950"> Fuir </button>
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
import SkillsPopup from './skillsPopup.vue'

export default {
  components: {
    result,
    FightInfos,
    PokemonStatus,
    SkillsPopup
  },
  props: {
    choosenPkm: Object,
  },
  data() {
    return {
      ennemyCharacter: ennemyData[0],
      textFightInfo : "",
      startFightAction : false,
      openActionPopup : false,
      healCount: 0, // Compteur pour limiter les soins à 3 fois
      victory: 0,
      shayminIsHere: false
    };
  },
  methods: {
    updateFightInfos(text: string) {
        this.textFightInfo = text
    },
    attack(skillInfo: object) {
      this.openActionPopup = false
      this.startFightAction = true
      // Attaque du joueur sur l'ennemi
      this.attackAction(this.choosenPkm, skillInfo, this.ennemyCharacter)
      // Vérifier si l'ennemi est vaincu
      this.checkIfIsStillAlive(this.ennemyCharacter.health, true)
      
      const enemyskill = this.ennemyCharacter.attacks[Math.floor(Math.random() * 2)]
      setTimeout(() => {
        // Attaque de l'ennemi sur le joueur
        this.attackAction(this.ennemyCharacter, enemyskill, this.choosenPkm)
        // Vérifier si le joueur est vaincu
        this.checkIfIsStillAlive(this.choosenPkm!.health, false)

      }, 2000)
      
      setTimeout(() => {
        this.startFightAction = false
      }, 4000)
    },
    attackAction(fighter: any, fighterAtq: any, victim: any){
      let fighterDamage = fighterAtq.dgts
      if(fighterAtq.type == victim.faiblesse){
        fighterDamage = fighterDamage*2
      } else if(fighterAtq.type == victim.resistance){
        fighterDamage = fighterDamage/2
      }
      victim.health -= fighterDamage;
        this.updateFightInfos(`${fighter.name} utilise ${fighterAtq.name} sur ${victim.name} et lui inflige ${fighterDamage} dégâts.`)
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

        if(this.choosenPkm!.health == this.choosenPkm!.maxhealth){
          this.updateFightInfos(`${this.choosenPkm!.name} a déjà ses PV au maximum. `)
        }else{
          this.updateFightInfos(`${this.choosenPkm!.name} se soigne de ${healingAmount} PV !`)
          // Limiter les soins à 3 fois
          this.healCount++;
        }
      }
      
      setTimeout(() => {
        this.startFightAction = false
      }, 2000)
    },

    handleCharacterDefeated() {
      this.victory = 2; // Défaite
    },
    handleEnemyDefeated() {
      this.victory = 1; // Victoire
    },
    LegendaryAppear() {
      this.shayminIsHere = true
      this.ennemyCharacter = ennemyData[1]
      this.startFightAction = true
      this.updateFightInfos('Le pokemon gratitude est arrivé !')
      this.choosenPkm!.health = this.choosenPkm!.maxhealth
      setTimeout(() => { 
        this.startFightAction = false
      }, 3000)
      
    },
    LetsBeatShaymin(){
      this.startFightAction = true
      this.updateFightInfos('vous avez carressé '+ this.choosenPkm!.name +' !')
      setTimeout(() => { 
        this.updateFightInfos(this.choosenPkm!.name + ' prend son courage et assène un coup énorme ! ')
        this.ennemyCharacter.health = 0
      }, 3000)

      setTimeout(() =>{
        this.victory = 3;
      }, 6000)
    }
  },

};
</script>
