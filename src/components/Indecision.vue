<template>
  
<img
  :src="img"
  alt="image"
  width="250"
  height="250"
  v-if="img"> 

<img
  src="https://static.vecteezy.com/system/resources/previews/003/987/195/non_2x/abstract-blue-cyan-liquid-papercut-style-design-background-can-be-used-as-banner-motion-web-or-poster-vector.jpg"
  alt="image"
  width="250"
  height="250"
  v-else
  > 


  <div class="bg-dark"></div>
  <div class="indecision-container">

    <input type="text" placeholder="Hazme una pregunta!" v-model="question" >
    <br>
    <br>
    <p>Recuerda terminar con un signo de interrogacion</p>

    <div>
        <h2> {{question}} </h2>
        <h1 v-if="answer"> {{answer}} </h1>
        <h1 v-else> Bienvenido!! </h1>
    </div>

  </div>

</template>

<script>
export default {
     data() {
    return {
        question: null,
        answer: null,
        img: null
    }
   },
   methods: {

        async getAnswer(){
            this.answer = 'Pensando...'
            const {answer, image} = await fetch('https://yesno.wtf/api').then( resp => resp.json() )


            this.answer = answer
            this.img = image
            
        }

   },
   watch: {
        question(value, oldValue){
            if(!value.includes('?')) return

            //TODO: realizar peticion http
            this.getAnswer()
        }

        
   }

}
</script>

<style>

    img, .bg-dark {
        height: 100vh;
        left: 0px;
        max-height: 100%;
        max-width: 100%;
        position: fixed;
        top: 0px;
        width: 100vw;
    }

    .bg-dark {
        background-color: rgba(0, 0, 0, 0.4);
    }

    .indecision-container {
        position: relative;
        z-index: 99;
    }
    
    input {
        width: 250px;
        padding: 10px 15px;
        border-radius: 5px;
        border: none;
    }
    input:focus {
        outline: none;
    }

    p {
        color: white;
        font-size: 20px;
        margin-top: 0px;
    }

    h1, h2 {
        color: white;
    }
    
    h2 {
        margin-top: 150px;
    }

</style>