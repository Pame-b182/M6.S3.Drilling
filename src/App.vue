<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg bg-dark" data-bs-theme="dark">
      <div class="container-md">
        <a class="navbar-brand mx-auto" href="#">Tienda Bit-Game</a>
      </div>
    </nav>
    <div class="alert alert-info m-3" role="alert">
      <h4 class="alert-heading">¡Bienvenido!</h4>
      <hr>
      <p>A continuación encontrarás la lista de los juegos que prefieres.</p>
    </div>
    <!-- Aparte de invocar el componente "Games" lo alimento con la props "juegos" que no es un dato literal, 
    si no que viene del componente, por ello se usa ":" y  "arrayGames" es el dato en el componente padre, que esta entrando a la prop.
    Se escucha el evento "borrarGame", declarado en el componente hijo, con "@" y
    se llama al evento "deleteGame" creado en padre, que borrará el juego-->
    <Games
    :juegos="arrayGames"
    @borrarGame="deleteGame"></Games>
  </div>
</template>

<script>
import Games from '@/components/Games.vue'

export default {
  name: 'App',
  data(){
    return{
      arrayGames: ["Arena of valor", "Pokemon Unite", "Donkey Kong", "Heroes of the storm", "Valorant"]
    }
  },
  methods: {
    //Se crea el método "deleteGame" que borrará los juegos del array "arrayGames" declarados en "data".
    //Se recibe el index, llamado ahora "event", enviado por el componente hijo
    deleteGame(event){
      //Se aplica el método splice() que elimina el index, 1 a la vez
      this.arrayGames.splice(event,1)
    }
  },
  components: {
    Games,
  }
}
</script>

<style>

</style>
