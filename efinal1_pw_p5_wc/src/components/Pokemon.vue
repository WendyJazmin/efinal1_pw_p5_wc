<template>

<div class="container">
    <img v-if="imagen" v-bind:src="imagen" 
    alt="no se puede visualizar"/>
   
    <h1>{{titulo}}</h1>
  </div>
  
  
   
  </template>
  
  <script>
  
  export default {
  
      //props:['titulo','valor'],
  
      /**otra forma de declarar props */
      props:{
          titulo:String,
          imagen:String
      },
  
      data(){
          return{
              respuesta:this.titulo
            
          }
      },
  
      methods: {
        async consumirAPI(){
            const {answer,image}= await fetch('https://yesno.wtf/api').then(r=>r.json());
            console.log(answer);
            console.log(image);

            this.respuesta= answer==='yes'?'SI!!':'NO!!';

        }
    },
  
      
  }
  </script>
  
  <style scoped>
  
      button{
          background: rgb(98, 0, 173);
          color: white;
          border-radius: 5px;
      }
  
      button:hover{
          background-color: black;
      }
  
      h1{
          font-family: 'Baloo 2', sans-serif;
          color: rgb(9, 9, 111);
      }

      img{
        height: 100px;
        width: auto;
      }

      .container{

    display: inline-block;
    text-align: center;
    margin-left: 100px;
      }
    
  </style>