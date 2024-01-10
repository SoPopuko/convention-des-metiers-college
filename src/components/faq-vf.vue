<template>
  <div>
    <div class="inline-block">
        <div>
          <h1>Il faut etre bon en math </h1>
          <question :isTrue="False" />
        </div>
        <div style="border: blue 2px solid;">
          explication
        </div>
    </div>

    <div class="inline-block">
        <div>
          <h1>C'est difficile </h1>
          <question :isTrue="False" />
        </div>
        <div style="border: blue 2px solid;">
          explication
        </div>
    </div>

    <div class="inline-block">
        <div>
          <h1>Cela demande beaucoup de temps </h1>
          <question :isTrue="True" />
        </div>
        <div style="border: blue 2px solid;">
          explication
        </div>
    </div>

    <div class="inline-block">
        <div>
          <h1>Il faut etre patient </h1>
          <question :isTrue="True" />
        </div>
        <div style="border: blue 2px solid;">
          explication
        </div>
    </div>

    <div class="inline-block">
        <div>
          <h1>Il faut etre bon en anglais </h1>
          <question :isTrue="True" />
        </div>
        <div style="border: blue 2px solid;">
          explication
        </div>
    </div>

    <div class="inline-block">
        <div>
          <h1>Les developpeurs ressemblent aux hackers des films </h1>
          <question :isTrue="False" />
        </div>
        <div style="border: blue 2px solid;">
          explication
        </div>
    </div>

  </div>
</template>

<script>
import question from './question.vue';

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
