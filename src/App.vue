<template>
  <h1>Hi!</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
  <p> Reaction time: {{ score }}</p>
</template>

<script>
import Block from './components/Block.vue'


export default {
  name: 'App',
  components: { Block },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
    }
  },
  methods: {
    start() {
      this.delay = 1000 + (Math.random() * 1000)
      this.isPlaying = true
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
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
</style>
