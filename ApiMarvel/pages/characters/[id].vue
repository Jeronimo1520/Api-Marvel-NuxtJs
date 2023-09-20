<template>
    <v-container class="container">
        <v-card class="card">
            <v-card-title class="title" style="text-align: center; font-size:xx-large;  font-weight: bold;"> {{ characterApi[0].name
            }}</v-card-title>
            <v-img :src="characterApi[0].thumbnail.path + '.'
                + characterApi[0].thumbnail.extension" alt="Foto del personaje" class="character-image"></v-img>
            <v-card-text style="text-align: center; font-size:medium;  font-weight: bold;">
                <p>{{ characterApi[0].description }}</p> 
            </v-card-text>
            <v-card-text style="text-align: center; font-size: large;  font-weight: bold;">
                <p>Cantidad de comics: {{ characterApi[0].comics.available }}</p>
            </v-card-text>
            <v-card-text style="text-align: center; font-size: large;  font-weight: bold;">
                <p>Cantidad de series: {{ characterApi[0].series.available }}</p>
            </v-card-text>
            <v-card-text style="text-align: center; font-size: large;  font-weight: bold;">
                <p>Cantidad de stories: {{ characterApi[0].stories.available }}</p>
            </v-card-text>
            <v-card-text style="text-align: center; font-size: large;  font-weight: bold;  font-weight: bold;">
                <p>Cantidad de events: {{ characterApi[0].events.available }}</p>
            </v-card-text>
            <v-card-list style="text-align: center; font-size: large; font-weight: bold;  font-weight: bold;">
                <v-list-item v-if="characterApi[0].series.items && characterApi[0].series.items.length > 0"
                    v-for="(item, index) in characterApi[0].series.items.slice(0, 3)">
                    <!--Slice trae una nueva lista con solo 3 items-->
                    <v-list-item-title style="font-weight: bold;">{{ item.name }}</v-list-item-title>
                </v-list-item>
                <v-list-item v-else>
                    <v-list-item-title>No hay elementos en series.</v-list-item-title>
                </v-list-item>
            </v-card-list>
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
    border-radius: 50% !important;
    justify-content: center !important;
}

.title {
    font-size: 2em;
    font-weight: bold;
    text-align: center;
}

.card {
    background: linear-gradient(45deg, #1111, white) !important;
    border-color: black;
}

</style>