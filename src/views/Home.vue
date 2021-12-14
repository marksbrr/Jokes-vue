<template>
  <div class="home">
    <h1 class="main-text">Create joke</h1>
    <div>
      <CreateJoke @add-joke="addJoke" :jokes="jokes" />
    </div>
    <Jokes :deleteJoke="deleteJoke" :jokes="jokes" />

    <input
      class="input-field"
      placeholder="Search in jokes.."
      v-model="filterValue"
      @change="filteredJokes()"
    />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Jokes from "../components/Jokes.vue";
import CreateJoke from "../components/CreateJoke.vue";

type jokesType = {
  question: string;
  answer: string;
  id: number;
  isVisible: boolean;
};

export default defineComponent({
  name: "Home",
  data: () => ({
    jokes: {} as jokesType[],
    showAddJoke: false,
    filterValue: "",
  }),
  methods: {
    addJoke(joke: jokesType) {
      this.jokes = [...this.jokes, joke];
    },
    deleteJoke(id: number) {
      this.jokes = this.jokes.filter((joke) => joke.id !== id);
    },
    filteredJokes() {
      return this.jokes.filter((item) => {
        return item.question.indexOf(this.filterValue) !== -1;
      });
    },
  },
  created() {
    this.jokes = [
      {
        question: "What do you call an acid with an attitude?",
        answer: "A mean-o-acid!",
        id: 1,
        isVisible: true,
      },
      {
        question: "What do you call a priest who becomes a lawyer?",
        answer: "A father-in-law!",
        id: 2,
        isVisible: true,
      },
    ];
  },
  emits: [],

  components: {
    Jokes,
    CreateJoke,
  },
});
</script>

<style>
body {
  background-color: grey;
}
.main-text {
  margin-bottom: 10px;
}
</style>
