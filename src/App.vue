<template>
        
  <PokemonPage/>

</template>

<script>

import CaracolaMagica from './components/CaracolaMagica.vue';
import Contador from "./components/Contador.vue";

import PokemonPage from "./modules/pokemon/pages/PokemonPages.vue"


export default {
  //Options API
  name: "App",
  components: {
    Contador,
    CaracolaMagica,
    PokemonPage,
  },
};
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
