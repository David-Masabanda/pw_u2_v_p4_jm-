<template>
  <div class="calculadora">
    <label for="">Calculadora</label>
    <input class="pantalla" id="resultado" v-model="resultado" type="number" />

    <div class="botones">
      <button v-on:click="num(7)">7</button>
      <button v-on:click="num(8)">8</button>
      <button v-on:click="num(9)">9</button>

      <button class="operaciones" v-on:click="op((a, b) => a + b, 'suma')">
        +
      </button>

      <button v-on:click="num(4)">4</button>
      <button v-on:click="num(5)">5</button>
      <button v-on:click="num(6)">6</button>

      <button class="operaciones" v-on:click="op((a, b) => a - b, 'resta')">
        -
      </button>

      <button v-on:click="num(1)">1</button>
      <button v-on:click="num(2)">2</button>
      <button v-on:click="num(3)">3</button>

      <button
        class="operaciones"
        v-on:click="op((a, b) => a * b, 'multiplicacion')"
      >
        *
      </button>

      <button v-on:click="num(0)">0</button>
      <button class="limpiar" v-on:click="resetear()">AC</button>
      <button class="igual" v-on:click="igual()">=</button>

      <button class="operaciones" v-on:click="op((a, b) => a / b, 'division')">
        /
      </button>
    </div>
    <p></p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num1: 0,
      num2: 0,
      operacion: undefined,
      resultado: "",
      signo: "",
    };
  },
  methods: {
    num(numero) {
      this.resultado += numero;
    },
    op(funcion, operador) {
      this.signo = operador;
      this.operacion = funcion;
      this.num1 = parseInt(this.resultado);
      this.resultado = "";
    },
    igual() {
      this.num2 = parseInt(this.resultado);
      this.resolver();
    },
    resolver() {
      console.log("Metodo computado");
      if (this.operacion) {
        switch (this.signo) {
          case "suma":
            this.sumar;
            break;
          case "resta":
            this.restar;
            break;
          case "multiplicacion":
            this.multiplicar;
            break;
          case "division":
            this.dividir;
            break;
          default:
            break;
        }
      }
    },
    resetear() {
      this.num1 = 0;
      this.num2 = 0;
      this.operacion = undefined;
      this.resultado = "";
    },
  },
  computed: {
    sumar() {
      this.resultado = this.operacion(this.num1, this.num2);
    },
    restar() {
      this.resultado = this.operacion(this.num1, this.num2);
    },
    multiplicar() {
      this.resultado = this.operacion(this.num1, this.num2);
    },
    dividir() {
      this.resultado = this.operacion(this.num1, this.num2);
    },
  },
};
</script>

<style>
.calculadora {
  width: 300px;
  margin: 0 auto;
  margin-top: 100px;
  padding: 20px;
  border: 2px solid gray;
  border-radius: 8px;
  background-color: rgb(240, 255, 255);
  /*background-image: url(../img/images.jpg);*/
}
.pantalla {
  width: 250px;
  font-size: 16px;
  border: 2px solid gray;
  border-radius: 5px;
  background-color: white;
  margin-bottom: 12px;
  margin-left: 10px;
}
.botones {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 10px;
}
button {
  padding: 15px;
  font-size: 16px;
  border-radius: 5px;
  background-color: #e0e0e0;
}
.operaciones {
  margin-left: 10px;
  border: 2px solid white;
  background-color: rgb(221, 158, 158);
}
.limpiar {
  border: 2px solid white;
  background-color: rgb(255, 99, 51);
}
.igual {
  border: 2px solid white;
  background-color: rgb(112, 128, 144);
}
button:hover {
  background-color: rgb(176, 196, 222);
}
label {
  font-size: 20px;
  color: #333;
  font-weight: bold;
  margin-bottom: 10px;
  display: block;
  text-align: center;
}
</style>