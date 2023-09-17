<template>
    <v-card>
        <v-img :src="character.thumbnail.path + '.' + character.thumbnail.extension"></v-img>
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