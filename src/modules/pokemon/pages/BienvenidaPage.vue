<template>
    <div class="bienvenida">
        <h1>Bienvenido Jugador</h1>
        <h3>Puede desplazarse por la barra superior para conocer mas sobre nuestro sitio.</h3>
        <h2>JUEGO</h2>
        <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSxuwDqLKnbQRSlIinWLE4-Y5LP55TiboDMOA&usqp=CAU" alt="">
        <h3>Obtendra informacion adicional, asi como las reglas del juego.</h3>
        <h2>PREMIOS</h2>
        <img src="https://kekentalento.com/wp-content/uploads/2021/12/NAVIDAD-1.jpg" alt="">
        <h3>Gran variedad de premios de alta calidad y valor.</h3>
        <h2>POKEMON</h2>
        <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/98/International_Pok%C3%A9mon_logo.svg/800px-International_Pok%C3%A9mon_logo.svg.png" alt="">
        <h3>El juego estara activo nada mas presione esta opcion, solo espere la carga inicial.</h3>
        

    </div>
</template>

<script>
export default {

}
</script>

<style scoped>

.bienvenida{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    background-image: url("https://guiasdevideojuegos.com/wp-content/uploads/2020/02/1-1024x576.jpg");
    background-size: cover;
    opacity: 0.8;
}

h1,h3,h2{
    color: aliceblue;
}


img{
    height: 200px;
    width: 250px;
}
</style>