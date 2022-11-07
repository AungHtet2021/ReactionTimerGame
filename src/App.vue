<template>
<h1>How fast can u catch me?</h1>
<button @click="start" :disabled="isPlaying">play</button>
<div v-if="isPlaying">
  <Block v-bind:delay="delay" @endGame="endGame"/>
</div>
  <div v-if="end">
    <Result :score="score" />
  </div>
</template>

<script>
import Block from "./components/Block.vue"
import Result from "./components/Result.vue"
export default {
  name: 'App',
  components: {
    Block,
    Result
  },
  data(){
    return{
      isPlaying:false,
      delay:null,
      score:0,
      end:false
    }
    },
  methods:{
      start(){
          this.isPlaying=true;
          this.delay=2000+Math.random()*5000;
          this.end=false;
      },
      endGame(score){
          this.score=score;
          this.isPlaying=false;
          this.end=true;
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
button {
  background-color: #7d2929; /* Green */
  border-radius: 10px;
  color: white;
  padding: 15px 32px;
  text-align: center;
  text-decoration: aqua;
  display:inline-block;
  font-size: 25px;
  font-style: italic;
}
</style>
