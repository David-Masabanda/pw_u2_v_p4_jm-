<template>
  <div class="game">
    <h1 v-if="!pokemonCorrecto">Espere por favor...</h1>
    <div v-else>
      <h1>Juego Pokemon</h1>

      <PokemonImg
        :pokemonId="pokemonCorrecto.id"
        :muestraPokemon="showPokemon"
      />

      <PokemonOps :opciones="arreglo" @seleccionar="revisarSeleccion($event)" />
      <Button @click="reset">Reiniciar</Button>
      <label for="">Puntaje: {{score}}</label>
    </div>
  </div>
</template>

<script>
import PokemonImg from "../components/PokemonImg.vue";
import PokemonOps from "../components/PokemonOps.vue";
import obtenerFachadaPokemons from "../helpers/clientePokemonAPI";

console.log(obtenerFachadaPokemons());

export default {
  data() {
    return {
      arreglo: [],
      pokemonCorrecto: null,
      showPokemon: false,
      score:0
    };
  },
  components: {
    PokemonImg,
    PokemonOps,
  },
  methods: {
    async cargaJuegoInicial() {
      const arregloPokemons = await obtenerFachadaPokemons();
      this.arreglo = arregloPokemons;
      console.log(arregloPokemons);
      const indicePokemon = Math.floor(Math.random() * 4);
      this.pokemonCorrecto = this.arreglo[indicePokemon];
    },

    revisarSeleccion(idSeleccionado) {
      console.log("Evento padre");

      console.log(idSeleccionado);
      if (idSeleccionado == this.pokemonCorrecto.id) {
        this.showPokemon = true;
        this.score++
      } else {
        this.showPokemon = false;
      }
    },
    reset() {
      this.arreglo = [];
      this.pokemonCorrecto = null;
      this.showPokemon = false;
      this.cargaJuegoInicial()
    },
  },

  mounted() {
    console.log("Se monto el componente");
    this.cargaJuegoInicial();
  },
};
</script>

<style scoped>
.game {
  display: grid;
  justify-content: center;
  align-items: center;
}
h1 {
  color: aqua;
  margin-bottom: 10px;
  width: 100%;
}
</style>