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
    },
    methods: {
         
    },
    computed: {
        
    }
}


</script>

<style scoped>
  .score-board {

  }
</style>
