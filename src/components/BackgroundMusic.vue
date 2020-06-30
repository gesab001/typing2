<template lang="html">

  <section class="background-music">
      <audio autoplay>
      <source src="horse.ogg" type="audio/ogg">
      <source src="https://raw.githubusercontent.com/gesab001/assets/master/music/tell-it-on-the-mountain.mp3" type="audio/mpeg">
    Your browser does not support the audio element.
    </audio> 
  </section>

</template>

<script lang="js">

  export default  {
    name: 'background-music',
    props: [],
    mounted () {

    },
    data () {
      return {

      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .background-music {

  }
</style>
