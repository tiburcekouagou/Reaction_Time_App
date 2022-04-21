<template>
  <h1 class="text-center font-bold text-3xl mt-10 text-gray-500">Reaction Timer App</h1>
  <button @click="start" class="bg-gray-200 hover:bg-gray-300 block my-4 mx-auto outline-none disabled:opacity-50 hover:disabled:cursor-not-allowed px-4 py-3 shadow-lg shadow-gray-400" :disabled="isPlaying">Start Game</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResult" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResult = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResult = true;
    },
  },
  mounted() {},
  components: { Block, Results },
};
</script>
