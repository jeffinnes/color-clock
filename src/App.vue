<template>
  <clock />
  <userInput />
</template>

<script>
import clock from './components/clock.vue';
import userInput from './components/userInput';

export default {
  name: 'App',
  components: {
    clock,
    userInput,
  }
}
</script>

<style>
html, body {
  height: 100%;
  margin: 0;
  font-size: 10px;
}
#app {
  font-family: "GeosansLight-NMS", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  grid-template-rows: 2fr 1fr;
  height: 100%;
}
</style>
