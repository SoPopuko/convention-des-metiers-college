<template>
    <div>
      <h1>Il faut etre bon en math ?</h1>
      <question :isTrue="trueOrFalse" />

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
        trueOrFalse: true,
      };
    },
  };
  </script>