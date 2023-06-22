<template>
  <h1>Caracola Magica</h1>
  <img src="https://www.tuexperto.com/wp-content/uploads/2022/01/paginas-descargar-fondos-de-pantalla.jpg" alt="No se puede cargar la imagen">
    <input v-model="pregunta" type="text" placeholder="Hazme una pregunta">
    <p>Recuerda terminar con un enter la pregunta</p>
    
    <div>
        <h2>Voy a pasar de año??</h2>
        <h1>SI, NO</h1>
    </div>


</template>

<script>
export default {
    data(){
        pregunta:'Hola Mundo'
    }
}
</script>

<style>

</style>