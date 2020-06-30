<template lang="html">

  <section >
    <SoundEffects id="popsound" v-if="playBallonPop"/>
    <div class="snackbar" v-if="showscore">{{score}}</div>
    <div v-bind:style="[styleObject]"> <h1>{{letter}}</h1></div>

  </section>

</template>

<script lang="js">
  import SoundEffects from './SoundEffects.vue'
  export default  {
    name: 'ballon',
    props: {letter: String},
    components: {SoundEffects},
    data: function() { 
      return {
        styleObject: {
             color: 'black',
             background: 'red',
             width: '50px',
             height: '50px',
             borderRadius: '50px',
             lineHeight: '10px', 
             position: 'fixed',
             textAlign: 'center',
             left: (Math.floor(Math.random() * 90)).toString() + '%',
             display: 'block',    
             bottom: this.bottom
              
        },
        bottom: 0,
        speed: 100,
        showscore: false,
        score: 0,
        playBallonPop: false

      }
    },
    created() {
        this.paintBallon();
        window.addEventListener('keyup', (e) => {
            if(this.letter==e.key & this.bottom>-10){
                  this.popBallon();
                  this.addScore();
                 


            }else{ 
                 this.score = 0;
                 this.showscore = false;
                 this.playBallonPop = false;
                 
            }

        });
       this.startInterval();
 
    },
    methods: {
        startInterval() {
            setInterval(() => {
                this.bottom++;
                this.styleObject.bottom = this.bottom + 'px';
                this.speed = this.speed - 100;
              
            }, this.speed)
        },
        paintBallon(){
           var colors = ['red', 'orange', 'yellow', 'green', 'blue', 'purple', 'pink'];
           this.styleObject.background = colors[(Math.floor(Math.random() * colors.length))];  
        },
        popBallon(){
            this.playBallonPop = true;
            this.bottom = -60
            this.styleObject.bottom = this.bottom + 'px';
            this.styleObject.left = (Math.floor(Math.random() * 90)).toString() + '%';
            this.paintBallon();

           
            
        },
        addScore(){
            this.score = localStorage.getItem("score");
            this.score++; 
            this.showscore = true;
            localStorage.setItem("score", this.score); 
        },
        initializeScore(){
           this.score = 0;
           localStorage.setItem("score", 0);
        }
    }
  
}


</script>

<style scoped>
.ballon {
     
     
     
}

#snackbar {
  min-width: 250px;
  margin-left: -125px;
  background-color: #333;
  color: #fff;
  text-align: center;
  border-radius: 2px;
  padding: 16px;
  position: fixed;
  z-index: 1;
  left: 50%;
  bottom: 30px;
  font-size: 17px;
}

#snackbar.show {
  visibility: visible;
  -webkit-animation: fadein 0.5s, fadeout 0.5s 2.5s;
  animation: fadein 0.5s, fadeout 0.5s 2.5s;
}

@-webkit-keyframes fadein {
  from {top: 0; opacity: 0;} 
  to {top: 30px; opacity: 1;}
}

@keyframes fadein {
  from {top: 0; opacity: 0;}
  to {top: 30px; opacity: 1;}
}

@-webkit-keyframes fadeout {
  from {top: 30px; opacity: 1;} 
  to {top: 0; opacity: 0;}
}

@keyframes fadeout {
  from {top: 30px; opacity: 1;}
  to {top: 0; opacity: 0;}
}
</style>
