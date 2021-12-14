<template>
  <button class="button">{{ text }}</button>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: String,
  },
};
</script>

<style scoped>
.button {
  border: none;
  border-radius: 5px;
  padding: 5px;
  margin: 5px;
  color: #000;
  font-size: 14px;
  font-weight: bold;
  transition: opacity 0.5s;
}
.button:hover {
  cursor: pointer;
  opacity: 0.5;
}
</style>
