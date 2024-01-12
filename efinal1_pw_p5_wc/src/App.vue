<template>
  <h1>JUEGO CASINO</h1>
  <p>Puntaje: {{ puntaje }} Intento: {{ intent0 }}</p>
  <div>
    <Pokemon ref="pokemon1" titulo="xxx" imagen="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/1.svg"/>
    <Pokemon ref="pokemon2" titulo="xxx" imagen="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/2.svg"/>
    <Pokemon  ref="pokemon3" titulo="xxx" imagen="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/3.svg"/>
  </div>
  
  <button @click="jugar">JUGAR</button>

</template>

<script>
import Pokemon from './components/Pokemon.vue'

export default {
  name: 'App',
  components: {
    Pokemon
  },

  data(){
    return{
      puntaje:0,
      intent0:0,
    }
   
  },

  methods: {
    async jugar() {
      this.intento++;
      Pokemon.imagen=
      // Llamar al método consumirAPI en cada componente Pokemon
      await Promise.all([
        this.$refs.pokemon1.consumirAPI(),
        this.$refs.pokemon2.consumirAPI(),
        this.$refs.pokemon3.consumirAPI()
      ]);
    },

    async consumirAPI(){
            const {answer,image}= await fetch('https://yesno.wtf/api').then(r=>r.json());
            console.log(answer);
            console.log(image);

            this.respuesta= answer==='yes'?'SI!!':'NO!!';

        }

  
  
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


</style>
