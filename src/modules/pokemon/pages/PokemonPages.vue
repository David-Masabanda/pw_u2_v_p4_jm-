<template>
  <div class="game">
    <h1 class="smsCarga" v-if="!pokemonCorrecto">Espere por favor...</h1>
    <div v-else class="estructura">
      <h1>Juego Pokemon</h1>
      <label class="puntos" for="">Puntaje: {{ score }}</label>
      <PokemonImg :pokemonId="pokemonCorrecto.id" :muestraPokemon="showPokemon" />

      <PokemonOps :opciones="arreglo" @seleccionar="revisarSeleccion($event)" />

      <Button v-show="intentos == 3 || acertoPokemon" @click="reset">Reiniciar</Button>
      <label for="">Intento: {{ intentos }}</label> <br>

      <label class="nombreCorrecto" v-show="intentos == 3 && error" for="">El Pokemon era: {{ pokemonCorrecto.nombre
      }}</label><br>

      <label v-show="error" class="erroneo" for="">El juego ha terminado, inténtalo nuevamente</label><br>
      <label v-show="acertoPokemon" class="acertado" for="">Felicitaciones, ¡has ganado!</label>
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
      score: 0,
      intentos: 0,
      acertoPokemon: false,
      error: false

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
      this.intentos++;
      console.log(idSeleccionado);
      if (idSeleccionado == this.pokemonCorrecto.id) {
        this.showPokemon = true;
        if (this.intentos === 1) {
          this.score += 5;
        } else if (this.intentos === 2) {
          this.score += 2;
        } else if (this.intentos === 3) {
          this.score += 1;
        }
        this.acertoPokemon = true;
      } else if (this.intentos === 3 && this.score === 0) {
        this.showPokemon = false;
        this.error = true
      }
    },
    reset() {
      this.arreglo = [];
      this.pokemonCorrecto = null;
      this.showPokemon = false;
      this.intentos = 0;
      this.acertoPokemon = false;
      this.score = 0;
      this.intentos = 0;
      this.acertoPokemon = false;
      this.error = false;
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
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  text-align: center;
}

h1 {
  color: rgb(220, 124, 83);
  margin-bottom: 10px;
  width: 100%;
  justify-content: center;
}

.smsCarga {
  color: black;
}

.estructura {
  margin-left: auto;
  margin-right: auto;
}

.puntos {
  font-weight: bold;
  font-size: 20px;
}

.erroneo {
  color: rgb(221, 92, 92);
  font-weight: bold;
  font-size: 20px;
}

.acertado {
  color: rgb(147, 147, 232);
  font-weight: bold;
  font-size: 20px;
}

.nombreCorrecto {
  margin-bottom: 20px;
  font-weight: bold;
  font-size: 15px;
}
</style>