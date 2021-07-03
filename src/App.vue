<template>
  <h1>Reaction Timer</h1>
  <div class="play-area" v-if="!isPlaying" @click="start" :disabled="isPlaying">Click To Start</div>
  <Block v-if="isPlaying" :delay="delay" @stop="showResults" />
  <Results v-if="donePlaying" :reactionTime="reactionTime"/>
</template>

<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue';

export default {
  name: 'App',
  components: {
    Block,
    Results,
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      reactionTime: null,
      donePlaying: false,
    }
  },
  methods: {
    start() {
      this.delay =  7000 + Math.random() * 3000;
      this.isPlaying = true;
      this.donePlaying = false;
    },
    showResults(reactionTime) {
      this.isPlaying = false;
      this.reactionTime = reactionTime;
      this.donePlaying = true;
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
