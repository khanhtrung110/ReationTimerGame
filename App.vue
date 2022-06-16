<template>
 <h1>Game Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Start</button>
  <Block v-if="isPlaying"  :delay = "delay" @end="endGame"/>
  <Results v-if="isShowBlock" :score="score"/>
</template>


<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
  name: 'App',
  data(){
    return{
    isPlaying: false,
    delay: null,
    score: 0,
    isShowBlock : false
    }
  },
  components: {
    Block,Results
  },
  methods:{
    start(){
      this.isPlaying = true;
      this.delay = 2000 + Math.random()*5000;
      this.isShowBlock = false
    },
    endGame(reationTime){
      this.score = reationTime
      this.isShowBlock = true
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
  color: gray;
  margin-top: 60px;
}
button{
  background: lightskyblue;
    padding: 10px 15px;
    border: 1px solid lightblue;
    border-radius: 10px;
}
</style>
