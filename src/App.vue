<template>
 <h1>Reaction Timer </h1>
 <button @click="start" :disabled="isPlaying">Play</button>
 <my-block :delay="delay" v-if="isPlaying" @end="endGame"></my-block>
 <my-results :score="score" v-if="showResults"></my-results>
</template>

<script>


import MyBlock from './components/my-block.vue';
import MyResults from './components/my-results.vue';
export default {
  name: 'App',
  data(){
   return{
    isPlaying: false,
    delay: null,
    score: null,
    showResults: false
   }
  },
  components: {
    MyBlock,
    MyResults
  },
  methods:{
    start(){
       this.delay = 2000 + Math.random() * 5000;
       this.isPlaying = true;
       console.log(this.delay);
    },
    endGame(reactionTime){
      this.isPlaying = false;
      this.score = reactionTime;
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
  color: #444;
  margin-top: 60px;
}
button{
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled]{
  cursor: not-allowed;
  opacity: 0.2
}
</style>
