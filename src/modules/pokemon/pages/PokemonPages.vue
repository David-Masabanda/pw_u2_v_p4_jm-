<template>
  <h1>Juego Pokemon</h1>

  <PokemonImg :pokemonId="25" :muestraPokemon="false" />

  <PokemonOps :opciones="arreglo"/>

</template>

<script>
import PokemonImg from "../components/PokemonImg.vue";
import PokemonOps from "../components/PokemonOps.vue";
import obtenerFachadaPokemons from "../helpers/clientePokemonAPI";

console.log(obtenerFachadaPokemons());

export default {
  data(){
    return{
      arreglo:[],
    };
  },
  components: {
    PokemonImg,
    PokemonOps,
  
  },
  methods: {
    async cargaJuegoInicial() {
      const arregloPokemons=await obtenerFachadaPokemons();
      this.arreglo=arregloPokemons;
      console.log(arregloPokemons);
    },
  },

  mounted() {
    console.log("Se monto el componente");
    this.cargaJuegoInicial()
  },
};
</script>

<style scoped>
h1 {
  color: aqua;
  margin-bottom: 10px;
  width: 70%;
}
</style>