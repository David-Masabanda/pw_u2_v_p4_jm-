<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  
  <Contador titulo="Profesor" valor2="15"></Contador>
  <Contador titulo="Estudiante"/>
</template>

<script>
import Contador from "./components/Contador.vue";

export default {
  //Options API
  name: "App",
  components: {
    Contador,
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
