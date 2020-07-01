<template lang="html">

  <section class="letter-input">
    <h1>Welcome to Typing Game</h1>
 



<input type="radio" id="two" value="choose" v-model="picked">
<label for="two">Choose</label>
<select v-model="selected">
  <option v-for="option in options" :key="option.id" v-bind:value="option.value">
    {{ option.text }}
  </option>
</select>
<p>or</p>
<input type="radio" id="one" value="create" v-model="picked">
<label for="one">Create</label>
   <input type="text" placeholder="enter characters to practice" @keyup.enter="startGame" @keyup="displayWord"> 
<br><button @click="startGame">start</button>
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
          selected: '',
          options: [
            { text: 'the quick brown fox jumps over the lazy dog', value: 'the quick brown fox jumps over the lazy dog' },
            { text: 'J, F, and Space', value: 'JF ' },
            { text: 'U, R, and K Keys', value: 'URK' },
            { text: 'D, E, and I Keys', value: 'DEI' },
            { text: 'C, G, and N Keys', value: 'CGN' },
            { text: 'T, S, and L Keys', value: 'TSL' },
            { text: 'O, B, and A Keys', value: 'OBA' },
            { text: 'V, H, and M Keys', value: 'VHM' },
            { text: 'Period and Comma', value: '.,' },
            { text: 'W, X, and ; Keys', value: 'WX;' },
            { text: 'Q and Y Keys', value: 'QY' },
            { text: 'Z and P Keys ', value: 'ZP' }
         ],
         picked: '',


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
        if (this.picked=="choose"){
              this.letters = this.selected
        } 
        if(this.letters==''){
           alert("please enter characters to practice or choose from the given options") 
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
