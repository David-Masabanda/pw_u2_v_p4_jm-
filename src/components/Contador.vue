<template>
  <h3>{{ evaluarTitulo }}</h3>
  <p>{{ numero }} <sup>2</sup>={{ obtenerCuadradroComputado }}</p>
  <p>{{ numero }} <sup>2</sup>={{ obtenerCuadradroComputado }}</p>
  <p>{{ numero }} <sup>2</sup>={{ obtenerCuadradroComputado }}</p>
  <button v-on:click="aumentar">+</button>
  <button @click="reducir">-</button>
</template>

<script>
export default {
  //Options API
  name: "Contador",
  data() {
    return {
      numero: this.inicio,
      tituloComponente: this.titulo,
    };
  },

  methods: {
    aumentar() {
      this.numero++;
    },
    reducir() {
      this.numero--;
    },

    obtenerCuadradro() {
      console.log("Entro al metodo obtener vcuadrado");
      return this.numero * this.numero;
    },
  },

  computed: {
    obtenerCuadradroComputado() {
      console.log("Entro al metodo obtener cuadrado computado");
      return this.numero * this.numero;
    },

    evaluarTitulo() {
      return this.tituloComponente || "valor por defecto";
    },
  },

  //Primera forma
  // props:['titulo','inicio']

  //Segunda forma
  props: {
    titulo: String,
    inicio: {
      type: Number,
      required: false,
      default: 100,
      validator(value) {
        return value > 100;
      },
    },
  },
};
</script>

<style>
button {
  background-color: #64b687;
  border-radius: 5px;
  border: 1px solid white;
  color: white;
  cursor: -moz-zoom-in;
  margin: 5px;
  padding: 5px 15px;
}
button:hover {
  background-color: rgb(169, 169, 169);
}
</style>