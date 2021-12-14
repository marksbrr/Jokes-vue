<template>
  <div class="random-joke-container">
    <h1 v-if="loading">Loading...</h1>
    <template v-else>
      <div
        class="random-joke-wrapper"
        v-for="({ joke }, index) in randomJokes"
        :key="joke"
      >
        <h2 class="random-joke">
          <div>
            <span>{{ index + 1 }}.</span>{{ joke }}
          </div>
        </h2>
      </div>
    </template>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import axios from "axios";

type JokesApi = {
  error: boolean;
  amount: number;
  jokes: [
    {
      category: string;
      type: string;
      joke: string;
      flags: {
        nsfw: boolean;
        religious: boolean;
        political: boolean;
        racist: boolean;
        sexist: boolean;
        explicit: boolean;
      };
      safe: boolean;
      id: number;
      lang: string;
    }
  ];
};
export default defineComponent({
  name: "RandomJokes",
  data: () => ({
    loading: true,
    randomJokes: [] as JokesApi[],
  }),
  created() {
    axios
      .get("https://v2.jokeapi.dev/joke/Programming?type=single&amount=10")
      .then(({ data }) => {
        this.randomJokes = data.jokes;
        this.loading = false;
      });
  },
});
</script>

<style>
.random-joke {
  margin: 10px;
}

.random-joke-container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.random-joke-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  max-width: 50vw;
  background: rgb(176, 235, 176);
  margin: 10px;
  border: 4px solid green;
  border-radius: 5px;
}
</style>
