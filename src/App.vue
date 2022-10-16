<template>
  <h1>Welcome to Reaction Timer!</h1>
  <p>Click on the screen when it becomes green.</p>
  <button :class="{playBtn: !isPlaying}" @click="start" :disabled="isPlaying">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/> 
  <Results v-if="showResults" :score="score" />
</template>

<script>
import Block from "./components/Block.vue"
import Results from "./components/Results.vue"

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
    Block,
    Results
  },
  methods: {
    start(){
      this.delay = 1500 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
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

.playBtn{
  padding: 20px 50px;
  background: #0faf87;
  color: white;
  border-radius: 5px;
  border: none;
  font-size: 1.25em;
  font-weight: bold;
  cursor: pointer;
}
.playBtn:hover{
  background: #0b7e61;
}
</style>
