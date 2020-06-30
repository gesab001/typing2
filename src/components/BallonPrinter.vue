<template lang="html">

  <section class="letter-input">
    <h1>Welcome to Typing Game</h1>
    <input type="text" placeholder="enter characters to practice" @keyup.enter="startGame" @keyup="displayWord"> <button @click="startGame">start</button>
    <p>{{letters}}</p>


  </section>

</template>

<script lang="js">

  export default  {
    name: 'letter-input',
    props: [],
    mounted () {

    },
    data () {
      return {
          letters: '',


      }
    },
    methods: {
      displayWord: function (event) {
        // now we have access to the native event
        event.preventDefault()
        this.letters = event.target.value;
        //this.$emit('childToParent', this.letters)

      },
     startGame: function (event) {
        // now we have access to the native event
        event.preventDefault()
        if(this.letters==''){
           alert("please enter characters to practice") 
        }else{
           this.$emit('childToParent', this.letters)
        }
      }
    },
    computed: {

    }
}


</script>

<style scoped>
  .letter-input {

  }
</style>
