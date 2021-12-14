<template>
  <div class="joke-container">
    <div class="joke" v-for="joke in jokes" :key="joke">
      <Joke :joke="joke" />

      <Button
        class="button"
        @click="joke.isVisible = !joke.isVisible"
        text="Tell me"
      />
      <Button class="button" @click="deleteJoke(joke.id)" text="Delete" />
    </div>
  </div>
</template>

<script>
import Button from "../components/Button.vue";
import Joke from "./Joke.vue";
export default {
  name: "Jokes",
  props: {
    jokes: Array,
    deleteJoke: Function,
  },
  components: {
    Button,
    Joke,
  },
};
</script>

<style scoped>
.joke-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.joke {
  background: green;
  width: 100%;
  max-width: 30vw;
  padding: 5px;
  margin: 5px;
  border: 2px solid white;
  border-radius: 5px;
  color: white;
}
</style>
