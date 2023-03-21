<template>
  <h1>The Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @showTime="getReactionTime" />
  <Results :reactionTime="reactionTime" v-if="reactionTime" />
</template>

<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue';

export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      reactionTime: null
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true;
    },
    getReactionTime(time) {
      this.reactionTime = time
      this.isPlaying = false
    }
  }
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
