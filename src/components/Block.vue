<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    Click Me
  </div>
</template>

<script>
export default {
  props: ['delay'],
  emits: ['end'],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    }
  },
  beforeMount() {
    console.log("before mount")
  },
  mounted() {
    console.log("mounted!")
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer() {
      clearInterval(this.timer)
      console.log(this.reactionTime)
      this.$emit('end', this.reactionTime)
    },
  }

}
</script>

<style>

.block {
  width: 400px;
  border-radius: 20px;
  background: lightcoral;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}

</style>