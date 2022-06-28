<template>
  <div id="app">
    <img id="logo" alt="Vue logo" src="./assets/logopokemon.png">
    <h2> Pokeguia</h2>
    <p> Nombre:<input type="text" v-model="nombrepokemon"><button v-on:click="buscarpokemon">Buscar</button></p>
    <Datos  v-bind:laImagen = "imagenpokemon"
            v-bind:listaMovimientos="arregloMovimientos"
            v-bind:listaHabilidades="arregloHabilidades"
            msg="Datos del Pokemon"/>
  </div>
</template>

<script>
import Datos from './components/Datos.vue'

export default {
  name: 'App',
  components: {
    Datos
  },
  data(){
    return{
        nombrepokemon: 'pikachu',
        imagenpokemon: '',
        arregloMovimientos:[],
        arregloHabilidades:[],
    }//fin return
  }, //fin data
  methods:{
    buscarpokemon(){
      this.limpiar();
      console.log(this.nombrepokemon);
      let elNombre = this.nombrepokemon;
      let url = 'https://pokeapi.co/api/v2/pokemon/'+elNombre;
      console.log(url);
      fetch(url)
      .then(response => response.json())
      .then(json =>{
        console.log(json);
        console.log(json.name);
        console.log(json.moves);
        console.log(json.abilities);

        this.imagenpokemon = json.sprites.front_default;
        for(let unMovimiento of json.moves){
            this.arregloMovimientos.push(unMovimiento);
        }

        for(let unaHabilidad of json.abilities){
            this.arregloHabilidades.push(unaHabilidad);
        }
        console.log("arregloMovimientos =>");
        console.log(this.arregloMovimientos);

      });
    },
    limpiar(){
      this.arregloMovimientos = [];
      this.arregloHabilidades = [];
    }, //fin limpiar
  }, //fin methods
  created(){
        this.buscarpokemon();
}, //fin created
}//fin export
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
#logo{
  width: 30%;
}
</style>
