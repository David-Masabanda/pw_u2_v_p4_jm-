<template>
  <div class="contenedorOpciones">
    <h3>Pokemon Opciones</h3>
    <ul>
      <!--<li>1</li>
      <li>2</li>
      <li>3</li>
      <li>4</li>-->
      <li v-for="pokemon in opciones" :key="pokemon.id" @click="$emit('seleccionar',pokemon.id)">{{pokemon.nombre}}</li>
    </ul>
  </div>
</template>

<script>
export default {


  props:{
    opciones:{
      type:Array,
      required:true
    }
  },

  methods:{
    pruebaDeEvento(){
      console.log("Prueba de evento")
    }
  }
};
</script>

<style scoped>
ul {
  list-style-type: none;
    display: flex;
  flex-direction: column;
  align-items: center;
  margin-left: -35px;
}
li {
  border: 1px solid rgb(153, 153, 241);
  border-radius: 5px;
  margin-bottom: 10px;
  background-color: bisque;
  width: 120px;
  cursor: pointer;
  text-align: center;
}
li:hover {
  background-color: rgb(235, 157, 112);
}
h3 {
  color: brown;
}
.contenedorOpciones{
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  margin-top: 35px;
}

</style>