<template>
  <div style="display: flex; flex-direction: column; align-items: center;">
    <div style="display: flex; align-items: center;">
      <h1>Il faut etre bon en math ?</h1>
      <question :isTrue="False" />
    </div>
    <div style="border: blue 2px solid;">
      explication
    </div>

    <div style="display: flex; align-items: center;">
      <h1>C'est difficile ?</h1>
      <question :isTrue="False" />
    </div>
    <div style="border: blue 2px solid;">
      explication
    </div>

    <div style="display: flex; align-items: center;">
      <h1>Cela demande beacoup de temps ?</h1>
      <question :isTrue="True" />
    </div>
    <div style="border: blue 2px solid;">
      explication
    </div>

    <div style="display: flex; align-items: center;">
      <h1>Il faut etre patience ?</h1>
      <question :isTrue="True" />
    </div>
    <div style="border: blue 2px solid;">
      explication
    </div>

    <div style="display: flex; align-items: center;">
      <h1>Il faut etre bon en anglais ?</h1>
      <question :isTrue="True" />
    </div>
    <div style="border: blue 2px solid;">
      explication
    </div>

    <div style="display: flex; align-items: center;">
      <h1>Les developpeurs ressemblent aux hackers des films ?</h1>
      <question :isTrue="False" />
    </div>
    <div style="border: blue 2px solid;">
      explication
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