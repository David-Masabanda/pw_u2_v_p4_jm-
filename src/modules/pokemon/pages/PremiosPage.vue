<template>
  <div class="premios">
    <h1>Premios</h1> <br>
    <h2>Estos son los premios que podrías ganar</h2>

    <div class="premio1">
      <h3>PlayStation 5</h3>
      <h4>Primer puesto</h4>
      <img class="consola"
        src="https://blackphonestorec.com/wp-content/uploads/2023/01/PS5.png" alt="">
    </div>
    <div class="premio2">
      <h3>Tablet Xiaomi</h3>
      <h4>Segundo Puesto</h4>
      <img class="tablet"
        src="https://marcimex.vtexassets.com/arquivos/ids/198586-800-auto?v=638137922781200000&width=800&height=auto&aspect=true"
        alt="">
    </div>
    <div class="premio3">
      <h3>Smartband</h3>
      <h4>Tercer puesto</h4>
      <img class="reloj" src="https://i01.appmifile.com/webfile/globalimg/products/m/mi-smart-band-6/section08.png"
        alt="">
    </div>

  </div>
</template>




<script>

export default {};

</script>




<style scoped>  
  .premios {
    display: grid;
    align-items: center;
    text-align: center;
   
    grid-template-columns: repeat(3, 5fr);
    background-color: rgb(219, 187, 145);
  }
  
  h1,h2{
    grid-column: 1/4;
  }

  img{
    width: 200px;
    height: 100px;
  }
  .premio1,  .premio2,  .premio3 {
    columns: 1;
    margin-top: 20px;
    padding: 20px;
    border: 1px solid #ccc;
    background-color: rgb(233, 230, 225);
  }


   img {
    width: 100%;
    height: auto;
    max-width: 100%;
    max-height: 100%;
  }
  h3{
    font-size: 30px;
  }

  h4 {
    font-weight: normal;
    font-size: 20px;
  }


  

</style>