<template>
    <v-card class="character-card">
        <v-img class="character-img" :src="character.thumbnail.path + '.' + character.thumbnail.extension"></v-img>
        <v-card-title>{{ character.name }}</v-card-title>
        <v-card-actions>
                <v-btn variant="outlined" @click="viewMore()">
                    Ver más
                </v-btn>
        </v-card-actions>
    </v-card>
</template>

<script setup>

const props = defineProps({
    character: {
        type: Object,
        required: true
    }
});

const router = useRouter();

const viewMore = () => {
    // Obtiene el id del character
    const characterId = props.character.id;

    // Navega a la ruta characters/{id}
    router.push({
        path: `/characters/${characterId}`,
    });
};
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