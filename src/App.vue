<template>
  <h1>Oz Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Start Game</button>
  <button v-if="!isPlaying" @click="showHow">How to Play?</button>
  <Result :score="score" v-if="showResults"></Result>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <HowToModal v-if="howTo" @close="showHow" />
</template>

<script>
import Block from "./components/Block.vue";
import HowToModal from "./components/HowToModal.vue";
import Result from "./components/Result.vue";

export default {
  name: "App",
  components: { Block, Result, HowToModal },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
      howTo: false,
    };
  },
  methods: {
    showHow() {
      this.howTo = !this.howTo;
    },
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.ended = true;
      this.showResults = false;
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
  background-color: seagreen;
  color: white;
  border-radius: 10px;
  border: 1px solid springgreen;
  padding: 0.5em 0.7em;
  margin: 10px;
}
button:disabled {
  background-color: rgb(168, 189, 177);
  border: none;
}
</style>
