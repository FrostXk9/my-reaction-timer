<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click Me
    </div>
    <div>{{ reactionTime }}</div>
    <div>Score {{ calculateScore() }}</div>
    <div>Speed {{ speed }}</div>
  </template>
  
  <script>
  export default {
      // Data that comes from App.vue that is passed down from the Block component
      props: ['delay'],
      data() {
        return {
          showBlock: false,
          timer: null,
          reactionTime: 0,
          speed: null,
        }
      },
      // This will execute as soon as this component is mounted to the dom (on the index.html in the div where the id="app")
      mounted() {
        // We are delaying the time it will take for the code to execute using the prop, delay  
        setTimeout(() => {
          // The div block is displayed after the delay is complete  
          this.showBlock = true;
          // We are calling the method here
          this.startTimer();
          // We are waiting for the delay time before the actions are performed above
        }, this.delay);  
        
      },
      methods: {
        startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);  
    },
    stopTimer() {
      clearInterval(this.timer);
      this.speed = this.calculateSpeed();
      console.log('done', this.reactionTime);
    },
    calculateSpeed() {
      if (this.reactionTime <= 200) {
        return "Very fast";
      } else if (this.reactionTime <= 400) {
        return "Relatively fast";
      } else {
        return "Not so fast";
      }
    },
    calculateScore() {
      return Math.floor(10000 / this.reactionTime);
    } 
      }
    }
  </script>
  
  <style>
      .block {
          width: 400px;
          border-radius: 20px;
          background: #0faf87;
          color: white;
          text-align: center;
          padding: 100px 0;
          margin: 40px auto;
      }
    </style>