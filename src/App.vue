<template>
  <h1>Reaction Game</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <Results v-if="showResults" :score="score"></Results>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'


export default {
  name: 'App',
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    }
  },
  methods: {
    start() {
      this.showResults = false
      this.delay = 1000 + (Math.random() * 1000)
      this.isPlaying = true
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  },
}
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
  background-color: lightcoral;
  color: white;
  border: none;
  padding: 8px 16px;
  margin: 10px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: button;
}

button[disabled] {
  opacity: 0.2;
}

button:hover {
  transform: scale(1.2);
}
</style>
