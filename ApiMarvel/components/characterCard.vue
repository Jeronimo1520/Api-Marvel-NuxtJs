<template>
    <v-card class="character-card">
        <v-img class="character-img" :src="character.thumbnail.path + '.' + character.thumbnail.extension"></v-img>
        <v-card-title>{{ character.name }}</v-card-title>
        <v-card-actions>
            <v-btn class="btn" variant="outlined" @click="viewMore()">
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
    /* Se establece un tamaño máximo para todas las imágenes */
    max-width: 100%;
    /* El ancho máximo será el 100% del contenedor (tarjeta) */
    max-height: 300px;
    /* Se stablece una altura máxima deseada */
    width: auto;
    /* Para mantener la proporcion de aspecto */
    height: auto;
    /* Para mantener la proporcion de aspecto */
}

.character-card {
    background-color: whitesmoke;
    border-color: black;
}

.btn:hover {

    background-color: rgb(163, 201, 234);
}
</style>