<template>

</template>

<script setup>
import axios from "axios";

const PUBLIC_API_KEY = 'cac443484e979ba71815a80c14030705';
const HASH = "426a36e6f780a1c9149fbd608ac5d007"

const characters = ref([])

const loadCharacters = async () => {
    const url = `https://gateway.marvel.com:443/v1/public/characters?limit=100&ts=1&apikey=${PUBLIC_API_KEY}&hash=${HASH}`;
    const { data } = await axios.get(url);
    characters.value = data
    console.log(data)
}

</script>