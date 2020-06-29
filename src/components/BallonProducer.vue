
<script>
import Ballon from './Ballon.vue'
export default {
  name: 'BallonProducer',
  components: {
    Ballon
  },
  props: {message: String},
  render: function (createElement) { 
    var elements = [];
    var total = this.letters.length
        for (var x=0; x<total; x++){
           var element = createElement(Ballon, {props: {letter: this.letters[x]}});
           elements.push(element);
        }
    return createElement(
      'div',
      elements
    )
  },
  data () {
      return {
      }
  },   
  created() {

    this.initializeLetters();
 
  },
  methods: {
      initializeLetters(){
         this.letters = this.removeDuplicates(this.message.split(""))

      },
      removeDuplicates(data){
         return data.filter((value, index) => data.indexOf(value) === index);

      },
      clickHandler(){
         alert("hello");
      }
  },


}
</script>

<style scoped>

</style>
