<template>
  <div>
    <div class="inline-block p-1 my-1">
        <div class="grid grid-cols-6 content-center bg-lime-900">
          <div class="col-span-5 text-2xl"> Il faut etre bon en maths </div>
          <question :isTrue="False" />
        </div>
        <div class="bg-stone-900 text-lg">
          <p>Pas forcément ! Etre bon en maths, c'est un plus, mais tant que tu as de la logique,
          tu peux aller tranquillement dans cette filière.</p>
          <b><u>Cours de maths en informatique:</u></b> algorithmique, suites, graphes, matrices
        </div>
    </div>

    <div class="inline-block p-1 my-1">
        <div class="grid grid-cols-6 content-center bg-lime-900">
          <div class="col-span-5 text-2xl">Cela demande du temps </div>
          <question :isTrue="True" />
        </div>
        <div class="bg-stone-900 text-lg">
          <p>Coder est une activité demandant beaucoup de temps: apprendre le langage, faire des exercices pour bien comprendre le fonctionnement...</p>
          <p>Développeur est un métier ou l'on apprends tout les jours tout change très vite et il faut s'adapter aux nouveautés.</p>
        </div>
    </div>

    <div class="inline-block p-1 my-3">
        <div class="grid grid-cols-6 content-center bg-lime-900">
          <div class="col-span-5 text-2xl">Il faut etre patient </div>
          <question :isTrue="True" />
        </div>
        <div class="bg-stone-900 text-lg">
         <p> Etre patient est <u>LA</u> qualité du développeur. Pourquoi ? parce que pour résoudre les probèmes,
          il faut parfois rester dessus pendant beaucoup (trop) de temps !</p>
        </div>
    </div>

    <div class="inline-block p-1 my-3">
        <div class="grid grid-cols-6 content-center bg-lime-900">
          <div class="col-span-5 text-2xl">Il faut etre bon en anglais </div>
          <question :isTrue="True" />
        </div>
        <div class="bg-stone-900 text-lg">
          <p>Presque tout ce qui touche au développement informatique est en anglais: le code (if, string, float, pull...)
          les modes d'emploi, les sites spécialisés, les tutoriels youtubes...</p>
        </div>
    </div>

    <div class="inline-block p-1 mt-3">
        <div class="grid grid-cols-6 content-center bg-lime-900">
          <div class="col-span-5 text-2xl">Developpeurs = Hackers de films </div>
          <question :isTrue="False" />
        </div>
        <div class="bg-stone-900 text-lg">
          <p><b>Absolument personne</b> ne tapote sur son clavier très vite en restant collé sur un écran rempli de vert et de noir.</p>
          <p>Les développeurs sont surtout des personnes qui tapent normalement sur leur clavier, font des recherches pour
          résoudre leurs problemes et participent à des réunions.</p>
        </div>
    </div>
  </div>
</template>

<script>
import question from './question.vue'

export default {
  components: {
    question,
  },
  data() {
    return {
      False: false,
      True: true,
    };
  },
};
</script>
