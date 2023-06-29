<template>
  <div class="contenedorOpciones">
    <h3>Pokemon Opciones</h3>
    <ul>
      <li>1</li>
      <li>2</li>
      <li>3</li>
      <li>4</li>
    </ul>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
ul {
  list-style-type: none;
}
li {
  border: 1px solid rgb(153, 153, 241);
  border-radius: 5px;
  margin-bottom: 10px;
  background-color: bisque;
  width: 100px;
  cursor: pointer;
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
}

</style>