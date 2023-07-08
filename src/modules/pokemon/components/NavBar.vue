<template>
  <div class="contenedor">
    <router-link to="/">Bienvenida</router-link >
    <router-link  to="/juego">Juego</router-link >
    <router-link  to="/premios">Premios</router-link >
    <router-link  to="/pokemon">Pokemon</router-link >
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.contenedor {
  display: flex;
  justify-content: center;
  padding: 0 30px;
}

.contenedor a {
  font-weight: bold;
  font-size: 20px;
  color: rgb(93, 80, 191);
  margin: 20px 10px;

}

</style>