<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <h1>Hello vue</h1>
  <TImerBtn />
</template>

<script>
import TImerBtn from './components/TImerBtn.vue';
export default {
  app(){
    return{
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false
    }
  },
  components : {
    TImerBtn,
  },
  methods: {
    start() {
      // Random number between 2000 and 7000 milliseconds
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
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
  color: #2c3e50;
  margin-top: 60px;
}
</style>
