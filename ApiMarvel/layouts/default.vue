<template>
  <v-card>
    <v-layout>

      <v-app-bar class="appbar" color="#ff171f">
        <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

        <!-- Mostrar el logotipo de Marvel en el centro -->
        <v-img src="https://1000marcas.net/wp-content/uploads/2021/07/Marvel-Comics-logo.png" max-height="48"
          class="marvel-logo"></v-img>

      </v-app-bar>

      <v-navigation-drawer v-model="drawer" location="left" temporary>
        <NuxtLink to="/">
          <v-list-item><v-icon icon="mdi-home" style="color: red;"/> Inicio </v-list-item>
        </NuxtLink>
        <NuxtLink to="/characters">
          <v-list-item><v-icon icon="mdi mdi-domino-mask" style="color: red;"/> Personajes </v-list-item>
        </NuxtLink>
      </v-navigation-drawer>
      <v-main class="main">
        <!-- slot: Carga el contenido de la página (pages/..) -->
        <slot />
      </v-main>
    </v-layout>
  </v-card>
</template>


<script setup>

const titleApp = ref("MARVEL CHARACTERS")


</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Marvel:wght@400;700&family=Roboto:wght@300&family=Signika&family=Ubuntu&display=swap');

.appbar {
  display: flex;
  align-items: center;
  text-align: center;
}

.main {
 background-color: rgb(210, 226, 240) !important;
}
</style>

<script>
export default {
  data: () => ({
    drawer: false,
  }),

  watch: {
    group() {
      this.drawer = false
    },
  },
}
</script>