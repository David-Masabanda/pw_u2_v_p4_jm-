<template>
  <h1>Juego Pokemon</h1>

  <PokemonImg :pokemonId="25" :muestraPokemon="false" />

  <PokemonOps />
</template>

<script>
import PokemonImg from "../components/PokemonImg.vue";
import PokemonOps from "../components/PokemonOps.vue";

export default {
  components: {
    PokemonImg,
    PokemonOps,
  },
};
</script>

<style>
h1 {
  color: aqua;
  margin-bottom: 10px;
}
</style>