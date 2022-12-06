<template>
  <h2 class="comp">{{title || customTitle }}</h2> 
  <!-- Condicion, si el componente no tiene la propiedad title, entonces se le agrega el metodo. -->
  <p>{{counter}}</p>

  <div>
    <button @click="incremento">+1</button>
    <button @click="decremento">-1</button>
  </div>
  <hr>
</template>

<script>
export default {
  props: {
    title: String,
    start: { 
      Number,
      default: 10,
      validator(value){
        return value > 100
      }
    }
  },
  data() {
    return {
        counter: this.start
    }
   },
   methods: {
      incremento(){
        this.counter = this.counter + 1;
      },
      decremento(){
       this.counter--
      }
   },
   computed: {
      customTitle(){

        return 'SALIERON'

      }
   }
}
</script>

<style>
  button{
    background-color: rgb(66, 160, 66);
    margin: 0 4px;
    color: azure;
    border-radius: 3px ;
  }
  .comp{
    background-color: rgb(161, 230, 161);
    margin: 0 5px;
    border-radius: 10px;

  }

</style>