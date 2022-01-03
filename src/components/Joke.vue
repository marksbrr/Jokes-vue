<template>
  <div>
    <h3 class="question-text">{{ joke.question }}</h3>
    <h3 v-if="!joke.isVisible">{{ joke.answer }}</h3>
  </div>
</template>

<script>
export default {
  name: "Joke",
  props: {
    joke: Object,
  },
  components: {},
};
</script>
<style>
.question-text {
  margin-bottom: 10px;
}
</style>
