<template>
    <v-container>
        <v-card class="card">
            <v-card-title class="title"> {{ characterApi[0].name }}</v-card-title>
            <v-img :src="characterApi[0].thumbnail.path + '.'
                + characterApi[0].thumbnail.extension" alt="Foto del personaje" class="character-image"></v-img>
            <v-card-text>
                <p>{{ characterApi[0].description }}</p>
            </v-card-text>
            <v-card-text>
                <p>* Cantidad de comics: {{ characterApi[0].comics.available }}</p>
            </v-card-text>
            <v-card-text>
                <p>* Cantidad de series: {{ characterApi[0].series.available }}</p>
            </v-card-text>
            <v-card-text>
                <p>* Cantidad de stories: {{ characterApi[0].stories.available }}</p>
            </v-card-text>
            <v-card-text>
                <p> * Cantidad de events: {{ characterApi[0].events.available }}</p>
            </v-card-text>
            <v-card-text>
                <ul v-for="i in [0, 1, 2]">
                    <li>
                        {{ characterApi[0].series.items[i].name }}
                    </li>
                </ul>
            </v-card-text>
        </v-card>
    </v-container>
</template>

<script setup>
const PUBLIC_API_KEY = 'cac443484e979ba71815a80c14030705';
const HASH = "426a36e6f780a1c9149fbd608ac5d007"
import axios from "axios";

const characterApi = ref([])
const route = useRoute();
const characterId = route.params.id


try {
    // const url = `https://gateway.marvel.com:443/v1/public/characters/${characterId}?${PUBLIC_API_KEY}`;
    const url = `https://gateway.marvel.com:443/v1/public/characters/${characterId}?&ts=1&apikey=${PUBLIC_API_KEY}&hash=${HASH}`
    const { data } = await axios.get(url);
    characterApi.value = data.data.results;
    console.log(characterApi);
} catch (error) {
    console.error("Error al cargar el personaje:", error);
}
</script>
<style>
.character-image {
    width: 100%;
    height: 200px;
    object-fit: cover;
}

.title {
    font-size: 2em;
    font-weight: bold;
    text-align: center;
}

.card{
     
}
</style>