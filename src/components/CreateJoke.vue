<template>
  <div class="joke__container">
    <form @submit.prevent="onSubmit">
      <div class="input__container">
        <h4 class="input-header">Question</h4>
        <input v-model="questionValue" class="input-field" />
      </div>
      <div class="input__container">
        <h4 class="input-header">Answer</h4>
        <input v-model="answerValue" class="input-field" />
      </div>
      <input type="submit" class="form__submit" value="Create" />
    </form>
  </div>
</template>

<script>
export default {
  name: "CreateJoke",
  props: {
    jokes: Object,
    addJoke: Function,
  },
  // eslint-disable-next-line @typescript-eslint/explicit-module-boundary-types
  data() {
    return {
      questionValue: "",
      answerValue: "",
    };
  },
  methods: {
    // eslint-disable-next-line @typescript-eslint/explicit-module-boundary-types
    onSubmit() {
      if (!this.questionValue) {
        alert(!this.questionValue && "Please add joke question");
        return;
      }

      if (!this.answerValue) {
        alert(!this.answerValue && "Please add joke answer");
        return;
      }

      const newJoke = {
        id: Math.floor(Math.random() * 9999),
        question: this.questionValue,
        answer: this.answerValue,
        isVisible: true,
      };
      this.$emit("add-joke", newJoke);

      this.questionValue = "";
      this.answerValue = "";
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
}

.joke__container {
  margin-bottom: 10px;
}

.input__container {
  margin-bottom: 10px;
}

.input-field {
  width: 100%;
  max-width: 20vw;
  padding: 5px;
  border-radius: 5px;
  border: none;
}

.form__submit {
  border: none;
  border-radius: 5px;
  padding: 5px;
  margin: 5px;
  background-color: #fff;
  font-size: 14px;
  font-weight: bold;
  transition: opacity 0.5s;
}
.form__submit:hover {
  cursor: pointer;
  opacity: 0.5;
}
.input-header {
  margin-bottom: 10px;
}
</style>
