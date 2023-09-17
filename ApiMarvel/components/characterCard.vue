<template>
    <v-card class="character-card">
        <v-img class="character-img" :src="character.thumbnail.path + '.' + character.thumbnail.extension"></v-img>
        <v-card-title>{{ character.name }}</v-card-title>
    </v-card>
</template>

<script setup>
const props = defineProps({
    character: {
        type: Object,
        required: true
    }
})
</script>
<style>
.character-img {
    width: 250px;
    height: 300px;
}

.character-card {
    width: 250px;
    background-color: #1111
}
</style>