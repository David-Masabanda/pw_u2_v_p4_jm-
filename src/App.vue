<template>

        

  <Ejercicio/>

</template>

<script>



import Ejercicio from './components/Ejercicio.vue';


export default {
  //Options API
  name: "App",
  components: {


    Ejercicio,
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
