<template>
  <div class="col col-md-6 mx-auto">
    <table class="table table-dark text-center">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Juego</th>
          <th scope="col">Eliminar juego de tu lista</th>
        </tr>
      </thead>
      <!-- Utilizo "v-for" para recorrer el array "arrayGames", me retorna un game y el index,
      que se encuentran en la prop "juegos". Y utilizo el "index" como la llave -->
      <tbody v-for="(game, index) in juegos" :key="index">
        <tr>
          <th scope="row">{{index}}</th>
          <td>{{game}}</td>
          <!-- El método "eliminarGame" recibe el index que provee el "v-for" para encontrar el juego que se quiere eliminar -->
          <td><button @click="eliminarGame(index)"  type="button" class="btn btn-danger">Eliminar</button></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "component-game",
  //Props recibe los datos externos
  //Para traer los datos que tiene el componente padre, debo utilizar props.
  //Este dato que llega lo tipeo como array y lo dejo como requerido.
  props: {
    juegos:{
      type: Array,
      required: true,
    }
  },
  data: function () {
    return {};
  },
  // computed: {},
  methods: {
    //Método que elimina el juego al que se le hizo click en el botón "eliminar"
    //entra el index, para poder ubicar cuál juego
    eliminarGame(index){
      //"this.$emit" emite  el evento (para que el padre lo escuche). 
      //1er argumento: nombre del evento. 2do argumento: le mando al padre el index, para que sepa cuál eliminar
      this.$emit('borrarGame', index)
    }
  }
  // watch: {},
  // components: {},
  // mixins: [],
  // filters: {},
  // -- Lifecycle Methods
  // -- End Lifecycle Methods
};
</script>

<style scoped>
</style>