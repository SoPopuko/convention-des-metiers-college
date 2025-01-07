<template>
    <div id="ennemy" class="flex flex-row-reverse">
        <div class="mt-20">
            <div id="ennemy-bar" class="flex m-2 w-40 h-5 border-slate-950 border-4 rounded-lg">
                <div v-for="index in enemyCharacter.health" :key="index" class="h-3 w-2 bg-red-500" />
            </div>
            <img class="w-32" src="/img/phyllali.png" />
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      enemyCharacter: { name: 'Phyllali', health: 72 }
    };
  },
  methods: {
    attack() {
      // Attaque de l'ennemi sur le joueur
      const enemyDamage = Math.floor(Math.random() * 5) + 1;
      this.controlledCharacter.health -= enemyDamage;
      console.log(`L'ennemi contre-attaque et inflige ${enemyDamage} dégâts au joueur.`);
    }
  }
};
</script>
