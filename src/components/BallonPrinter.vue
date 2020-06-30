<template lang="html">

  <section class="letter-input">
    <h1>Enter characters to practice</h1>

    <input @keyup.enter="submit"> <button @click="submit">start</button>


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
          letters: 'Jesus',


      }
    },
    methods: {
      submit: function (event) {
        // now we have access to the native event
        event.preventDefault()
        this.letters = event.target.value;
        this.$emit('childToParent', this.letters)

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
