<template  lang="html">
   <div >
      <BackgroundMusic/>
      <BallonPrinter v-if="showinput" v-on:childToParent="onReceivingMessage"/>
      <ScoreBoard v-if="showscoreboard"/>
      <BallonProducer  v-if="fly" :message="letters"/>
      <button v-if="newgame" v-on:click="createNewGame" >new word</button>
      <p>{{letters}}</p>
      <p>{{test}}</p>
   </div>

</template>

<script>

import BallonPrinter from './components/BallonPrinter.vue'
import BallonProducer from './components/BallonProducer.vue'
import ScoreBoard from './components/ScoreBoard.vue'
import BackgroundMusic from './components/BackgroundMusic.vue'
export default {
  name: 'App',
  components: {
    BallonPrinter,
    BallonProducer,
    ScoreBoard,
    BackgroundMusic
  },
  data () {
     return {
       letters: 'jesus',
       fly: false,
       showinput: true,
       newgame: false,
       showscoreboard: false
       
     }
  },
  methods: {
    onReceivingMessage(value) {
       this.letters = value
       this.fly = true
       this.showinput = false
       this.newgame = true
       localStorage.setItem("score", 0)
       this.showscoreboard = true
    
    },
    createNewGame() {
         this.showinput = true
         this.fly = false
         this.newgame = false,
         this.showscoreboard = false
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
