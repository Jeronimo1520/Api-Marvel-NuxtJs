<template class="template">
  <v-container class="container">
    <v-row>
      <v-col v-for="character in characters" :key="character.id" cols="12"
        sm="6"
        md="4"
        lg="3">
        <characterCard :character="character" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import axios from "axios";

const PUBLIC_API_KEY = 'cac443484e979ba71815a80c14030705';
const HASH = "426a36e6f780a1c9149fbd608ac5d007" 

const characters = ref([])

const loadCharacters = async () => {
  const url = `https://gateway.marvel.com:443/v1/public/characters?limit=100&nameStartsWith=spider&ts=1&apikey=${PUBLIC_API_KEY}&hash=${HASH}`;
  const { data } = await axios.get(url);
  // Filtrar los personajes que tienen una imagen disponible
  const charactersWithImages = data.data.results.filter(character => {
    return character.thumbnail.path != "http://i.annihil.us/u/prod/marvel/i/mg/b/40/image_not_available"
  });

  characters.value = charactersWithImages;
  console.log(charactersWithImages)
}

loadCharacters();
</script>
<style>

</style>