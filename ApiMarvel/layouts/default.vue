<template>
  <v-card>
    <v-layout>
      <!-- <v-system-bar color="deep-purple darken-3"></v-system-bar> -->

      <v-app-bar class="appbar" color="#518cca">
        <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

        <v-toolbar-title style="color: black; font-weight: 700;">{{ titleApp }}</v-toolbar-title>

      </v-app-bar>

      <v-navigation-drawer v-model="drawer" location="left" temporary>
        <v-list :items="items"></v-list>
      </v-navigation-drawer>
      <v-main class="align-center justify-center">
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

.appbar{
  display: flex; 
  align-items: center;
  text-align: center;
}

</style>

<script>
export default {
  data: () => ({
    drawer: false,
    group: null,
    items: [
      {
        title: 'Foo',
        value: 'foo',
      },
      {
        title: 'Bar',
        value: 'bar',
      },
      {
        title: 'Fizz',
        value: 'fizz',
      },
      {
        title: 'Buzz',
        value: 'buzz',
      },
    ],
  }),

  watch: {
    group() {
      this.drawer = false
    },
  },
}
</script>