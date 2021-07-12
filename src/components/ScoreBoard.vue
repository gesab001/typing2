<template lang="html">

  <section class="score-board">
    <h1>{{score}}</h1>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'score-board',
    props: [],
    mounted () {

    },
    data () {
      return {
         score: 0
      }
    },
    created(){
       
       var currentScore =  localStorage.getItem("score");
       if (currentScore==null){
          currentScore = 0;
       }
       this.score = currentScore;
       window.addEventListener('keyup', (e) => {
            console.log(e);
             this.updateScore();               

        });
               window.addEventListener('keydown', (e) => {
            console.log(e);
             this.updateScore();               

        });
       window.onstorage = () => {

           console.log(JSON.parse(window.localStorage.getItem('score')));
        };
    },
    methods: {
       updateScore(){
        var currentScore =  localStorage.getItem("score");
	if (currentScore==null){
		currentScore = 0;
	}
		this.score = currentScore;      
       }
         
    },
    computed: {
        
    }
}


</script>

<style scoped>
  .score-board {

  }
</style>
