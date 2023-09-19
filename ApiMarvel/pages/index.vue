<template>
    <div class="welcome-page">
      <center>
        <h1>Bienvenido</h1>
        <p>En este sitio web podrás visualizar personajes de Marvel y obtener más información sobre ellos</p>
        <NuxtLink to="/characters">
          <v-btn>
            Click para visualizar
          </v-btn>
        </NuxtLink>
      </center>
      <div class="background-image"></div>
    </div>
  </template>
  
  <script>
  export default {
    // Tu script aquí
  }
  </script>
  
  <style scoped>
  .welcome-page {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    text-align: center;
    color: #000000;
    position: relative;
    overflow: hidden;
  }
  
  .background-image {
    position: absolute;
    filter: blur(5px); /* Ajusta el valor de blur según lo que desees */
    z-index: -1;
    background-image: url('https://www.cartonionline.com/gif/FUMETTI/marvel/vendicatori/vendicatori_02.jpeg');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    width: 100vw;
    height: 100vh;
    opacity: 0.6; 
  }

  p{
    font-weight:bold ;
  }
  </style>
  