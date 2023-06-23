<template>
  <h1>Caracola Magica</h1>
  <img v-if="rutaImagen" :src="rutaImagen" alt="No se puede cargar la imagen" />

  <div class="fondo"></div>

  <div class="contenedor">
    <input v-model="pregunta" type="text" placeholder="Hazme una pregunta" />
    <p>Recuerda terminar con un enter la pregunta</p>

    <div>
      <h1>{{ pregunta }}</h1>
      <h2>{{ respuesta }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pregunta: "",
      respuesta: "",
      rutaImagen: null,
    };
  },
  watch: {
    pregunta(value, oldValue) {
      console.log(value);
      console.log(oldValue);
      if (value.includes("?")) {
        console.log("Consumir el API");
        this.consumirAPI();
      }
    },
  },

  methods: {
    async consumirAPI() {
      const respuesta = await fetch("https://yesno.wtf/api").then((r) =>
        r.json()
      );
      const { answer, image } = respuesta;
      console.log(answer);
      console.log(image);
      this.respuesta = answer;
      this.rutaImagen = image;
    },
  },
};
</script>

<style>
img,
.fondo {
  height: 100vh;
  width: 100vw;
  max-width: 100%;
  max-height: 100%;
  margin-bottom: 20px;
  left: 0px;
  position: fixed;
  top: 0px;
}

.fondo {
  background-color: rgba(0, 0, 0, 0.4);
}
.contenedor {
  position: relative;
}
input {
  width: 250px;
  padding: 10px 15px;
  border-radius: 5px;
  border: none;
}
p,h1,h2{
    color: azure;
}
p{
    font-size: 20px;
    margin-top: 0px;
}
</style>