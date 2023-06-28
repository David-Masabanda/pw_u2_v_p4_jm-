<template>
  <div class="container">
    <div class="adivinar">
      <label for="">Adivina cual es el pokemon</label>
      <img :src="rutaImagen" alt="No se puede mostrar" class="fotoPokemon" />
      <button class="opcion" @click="verificar('Pikachu')">Pikachu</button>
      <button class="opcion" @click="verificar('Blastoise')">Blastoise</button>
      <button class="opcion" @click="verificar('Beedrill')">Beedrill</button>
      <button class="opcion" @click="verificar('Charizard')">Charizard</button>
      <label id="respuesta" class="mensaje" v-if="mostrarMensaje">{{
        mensaje
      }}</label>
      <button id="reinicio" class="opcion" @click="reinicio()">Reinicio</button>
    </div>

    <div class="respuesta">
      <label for="">Respuesta:{{ respuesta }}</label>
      <img
        class="fotoRespuesta"
        v-if="rutaImagen"
        :src="rutaRespuesta"
        alt="No hay respuesta todavia"
      />
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      rutaImagen:
        "https://imgmedia.libero.pe/652x359/libero/original/2022/07/09/62ca1648c47fd170f4411671.webp",
      rutaRespuesta: null,
      respuesta: "",
      positivo: [],
      negativo: [],
    };
  },

  created() {
    this.crearArreglos();
  },

  methods: {
    
    reinicio() {
      this.rutaImagen =
          "https://imgmedia.libero.pe/652x359/libero/original/2022/07/09/62ca1648c47fd170f4411671.webp";
      this.rutaRespuesta = null;
      this.respuesta = "";
    
    },

    async verificar(pokemon) {
      if (pokemon === "Charizard") {
        this.rutaImagen =
          "https://www.nintenderos.com/wp-content/uploads/2020/12/pokemon-charizard.jpg";
        this.respuesta = " Acertaste";
        this.rutaRespuesta = this.positivo[0].image;
        this.positivo.shift();
      } else {
        this.rutaImagen =
          "https://imgmedia.libero.pe/652x359/libero/original/2022/07/09/62ca1648c47fd170f4411671.webp";
        this.respuesta = " Mas suerte para la proxima";
        this.rutaRespuesta = this.negativo[0].image;
        this.negativo.shift();
      }

      await this.consumirAPI();
    },

    async consumirAPI() {
      const respuesta = await fetch("https://yesno.wtf/api").then((r) =>
        r.json()
      );

      const { answer, image } = respuesta;

      if (answer == "yes") {
        this.positivo.push(respuesta);
      } else {
        this.negativo.push(respuesta);
      }
    },

    async crearArreglos() {
      while (this.positivo.length < 10 && this.negativo.length < 10) {
        await this.consumirAPI();
      }
    },
  },
};
</script>

<style>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.adivinar,
.respuesta {
  flex: 1;
  display: grid;
  background-color: rgb(240, 248, 255);
  margin-left: 25px;
  margin-right: auto;
  margin-top: 25px;
  font-size: 20px;
  border-radius: 15px;
  padding-bottom: 15px;
}

.fotoPokemon {
  width: 50%;
  display: block;
  margin: 0 auto 1px;
  border-radius: 15px;
  padding-bottom: 10px;
  padding-top: 12px;
}

.opcion {
  width: 25%;
  margin: 0 auto 5px;
  border-radius: 15px;
}

#reinicio {
  margin-top: 10px;
  background-color: rgb(245, 110, 103);
}

label {
  font-size: 20px;
  padding-top: 5px;
  font-weight: bold;
}

.respuesta {
  flex: 1;
}

.fotoRespuesta {
  width: 50%;
  display: block;
  margin: 0 auto 1px;
  border-radius: 15px;
  padding-bottom: 10px;
  padding-top: 12px;
}

body{
  background-image: url("https://i.ytimg.com/vi/l-wPToTDIHI/maxresdefault.jpg");
   background-size: cover;

}
</style>