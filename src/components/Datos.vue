<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <img v-bind:src="laImagen" alt="">
    <h2>Movimientos</h2>
    <ul>
      <li v-for="movimiento in listaMovimientos">
        {{ movimiento.move.name }}
      </li>
    </ul>

    <h2>Habilidades</h2>
    <ul>
      <li v-for="habilidad in listaHabilidades">
        {{ habilidad.ability.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'Datos',
  props: {
    msg: String,
    laImagen:'',
    listaMovimientos: [],
    listaHabilidades:[],
  },
  data(){
    return{
    otraLista:[
      {"mensaje": 'hola'},
      {"mensaje": 'chau'},
      {"mensaje": 'adios'},
    ],
    }//Fin return
  }//Fin data
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
