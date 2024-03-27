<template>
  <h1>Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @reaction="endGame" />
  <Result v-if="showResults" :score="score" />
</template>

<script>
import Block from "./components/Block-tab.vue";
import Result from "./components/Result-tab.vue";

export default {
  name: "App",
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  components: { Block, Result },
  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 5000;
      this.showResults = false;
      console.log(this.delay);
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button {
  padding: 10px 20px;
  font-size: 20px;
  background-color: #1a9fb3;
  color: #fff;
  border: none;
  border-radius: 50px;
  cursor: pointer;
}
button:disabled {
 opacity: 0.5;
  cursor: not-allowed;
}
</style>
