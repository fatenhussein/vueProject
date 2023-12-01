<template>
  <h1>ninga reaction timer</h1>

  <button @click="start" :disabled="isPlaying">play</button>
  <Block_component v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResults" :score="score"/>
  <!-- <p  v-if="showResults"  >reaction time:{{ score }} ms</p> -->


</template>

<script>
import Block_component from './components/Block_component.vue';
import Results from './components/Results_component.vue';
export default {
  name: 'App',
  components: {
    Block_component,
    Results
  },

  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults:false
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;

      console.log(this.delay);
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
</style>
