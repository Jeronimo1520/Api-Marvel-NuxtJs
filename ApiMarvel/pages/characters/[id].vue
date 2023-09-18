<template>
    <div>
        character: {{ $route.params.id}}
    </div>
    <v-container>
        <v-card>
            <v-card-title>{{ characterApi.name }}</v-card-title>
            <v-card-text>
                <p>{{ characterApi.description }}</p>
            </v-card-text>
        </v-card>
    </v-container>
</template>

<script setup>
const PUBLIC_API_KEY = 'cac443484e979ba71815a80c14030705';
const HASH = "426a36e6f780a1c9149fbd608ac5d007"
import axios from "axios";

const characterApi = ref({})
const route = useRoute();
const characterId = route.params.id
console.log(characterId)

const loadCharacter = async () => {
    // const url = `https://gateway.marvel.com:443/v1/public/characters/${characterId}?${PUBLIC_API_KEY}`;
    const url = `https://gateway.marvel.com:443/v1/public/characters/${characterId}?&ts=1&apikey=${PUBLIC_API_KEY}&hash=${HASH}`
    const { data } = await axios.get(url);
    characterApi.value = data;
    console.log(characterApi.data)
}
loadCharacter()
</script>