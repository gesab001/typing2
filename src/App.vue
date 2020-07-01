<template  lang="html">
   <div >
      <BackgroundMusic v-if="playbackgroundmusic"/>

      <BallonPrinter  v-if="showinput" v-on:childToParent="onReceivingMessage"/>

      <BallonProducer  v-if="fly" :message="letters"/>
      <button v-if="newgame" v-on:click="createNewGame" >new word</button>
   </div>

</template>

<script>

import BallonPrinter from './components/BallonPrinter.vue'
import BallonProducer from './components/BallonProducer.vue'
import BackgroundMusic from './components/BackgroundMusic.vue'
export default {
  name: 'App',
  components: {
    BallonPrinter,
    BallonProducer,
    BackgroundMusic
  },
  data () {
     return {
       letters: 'jesus',
       fly: false,
       showinput: true,
       newgame: false,
       showscoreboard: false,
       playbackgroundmusic: false
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
       this.playbackgroundmusic = true
       
    
    },
    createNewGame() {
         window.location.reload()
         this.showinput = true
         this.fly = false
         this.newgame = false,
         this.showscoreboard = false
         this.playbackgroundmusic = false
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
