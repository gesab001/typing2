<template lang="html">

  <section class="sound-effects">
     <audio autoplay>
      <source src="horse.ogg" type="audio/ogg">
      <source src="https://gesab001.github.io/assets/soundeffects/ballon-pop.mp3" type="audio/mpeg">
    Your browser does not support the audio element.
    </audio> 
  </section>

</template>

<script lang="js">

  export default  {
    name: 'sound-effects',
    props: [],
    mounted () {

    },
    data () {
      return {
        url: ''

      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .sound-effects {
     
  }
</style>
