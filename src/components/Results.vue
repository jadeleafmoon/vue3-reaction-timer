<template>
  <h3 class="rank">{{  rank }}</h3>
  <h4>Reaction time: {{ score }} ms</h4>
</template>

<script>

export default {
  props: ['score'],
  data() {
    return {
      rank: null,
    }
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "Ninja Fingers"
    } else if (this.score < 400) {
      this.rank = "Rapid Reflexes"
    } else {
      this.rank = "Snail pace ..."
    }
  }
}

</script>

<style>
.rank {
  font-size: 1.4em;
  color: lightcoral;
}
</style>