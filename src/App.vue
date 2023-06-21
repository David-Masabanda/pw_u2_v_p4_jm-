<template>
  <img alt="Vue logo" src="./assets/logo.png" />

  <Contador titulo="Profesor" v-bind:inicio="25+75"></Contador>
  <Contador titulo="Estudiante" :inicio="101"/>

</template>

<script>
import Calculadora from "./components/Calculadora.vue";
import Contador from "./components/Contador.vue";

export default {
  //Options API
  name: "App",
  components: {
    Contador,
    Calculadora,
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
