<template>
  <div>
      <div class="question">
        {{ questionData }}
      </ div>

      <div class="reponse">
        {{ reponseData }}
      </ div>
  </div>
</template>;

<script lang="js">
export default {
    data() {
        return {
            questionData: question,
            reponseData: reponse
        }
  },
  props() {
    question: String,
    reponse: String
  }
}
</script>
