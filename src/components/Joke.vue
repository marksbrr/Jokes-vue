<template>
  <div>
    <h3>{{ joke.question }}</h3>
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
<style></style>
