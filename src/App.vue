<template  lang="html">
   <div >
      <a href="https://www.typinggames.zone/web/resources/templates/frontend/typingmaster/keybricks5.htm?keys=abcdefghijklmnopqrstuvwxyz" target="_blank">keybricks</a><span>  |  </span>
            <a href="https://www.typinggames.zone/web/resources/templates/frontend/typingmaster/keytower/index2.html?keys=abcdefghijklmnopqrstuvwxyz" target="_blank">keytower</a><span>  |  </span>
                  <a href="https://www.typinggames.zone/web/resources/templates/frontend/typingmaster/typing-racer/car.htm" target="_blank">type racer  </a><span>  |  </span>
                  <a href="https://gesab001.github.io/bible">Bible</a><span>  |  </span>
                  <a href="https://gesab001.github.io/prayter-reactjs">Pray</a>
      <h1>HIGHEST SCORE: {{highestScore}}</h1>
      <button v-if="resetScoreButton" v-on:click="resetScore">Reset score</button>

      <BackgroundMusic v-if="playbackgroundmusic"/>

      <BallonPrinter  v-if="showinput" v-on:childToParent="onReceivingMessage"/>

      <BallonProducer  v-if="fly" :message="letters"/>
            <ScoreBoard v-if="fly"/>
      <button v-if="newgame" v-on:click="createNewGame" >new word</button>
   </div>

</template>

<script>

import BallonPrinter from './components/BallonPrinter.vue'
import BallonProducer from './components/BallonProducer.vue'
import BackgroundMusic from './components/BackgroundMusic.vue'
import ScoreBoard from './components/ScoreBoard.vue'
export default {
  name: 'App',
  components: {
    BallonPrinter,
    BallonProducer,
    BackgroundMusic,
    ScoreBoard
  },
  data () {
     return {
       letters: 'jesus',
       fly: false,
       showinput: true,
       newgame: false,
       showscoreboard: false,
       playbackgroundmusic: false,
       highestScore: 0,
       resetScoreButton: true,
     }
  },
  created() {

     this.highestScore = this.getHighestScore();
  },
  methods: {
    onReceivingMessage(value) {
       this.letters = value
       this.fly = true
       this.showinput = false
       this.newgame = true
       localStorage.setItem("score", 0)
       this.showscoreboard = true
       this.playbackgroundmusic = true,
       this.resetScorebutton = false
       
    
    },
    createNewGame() {
         window.location.reload()
         this.showinput = true
         this.fly = false
         this.newgame = false,
         this.showscoreboard = false
         this.playbackgroundmusic = false,
         this.resetScorebutton = true
      },
   getScoreTable(){
           var jsondata = JSON.parse(localStorage.getItem("scoretable"));
           return jsondata.scores;
        },
   getHighestScore(){
           var scoreList = this.getScoreTable();
           var highestScore = Math.max(...scoreList)
           return highestScore;
   },
   resetScore(){
      this.highestScore = 0;
      var scoretable = {"scores": [0]};
      localStorage.setItem("scoretable", JSON.stringify(scoretable)); 
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

#startgame{
    position:fixed;
    padding:0;
    margin:0;
    top:0;
    left:0;
    line-height: 100%;
    width: 100%;
    height: 100%;
    background: orange;
    


}
.vertical-center {
  position: absolute;
  top: 50%;
  -ms-transform: translateY(-50%);
  transform: translateY(-50%);
  text-align: center;
  border: 3px solid green;
}
.horizontal-center {
  margin-left: 35%;
  border: 3px solid #73AD21;
  padding: 10px;
}

</style>
