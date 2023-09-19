<template>
    <div>
        <center>
            <h1>Bienvenido a Personajes de Marvel</h1>
            <p>En este sitio web podras visualizar personajes de Marvel y mas informacion sobre ellos</p>
            <NuxtLink to="/characters">
                <v-btn>
                    Click para visualizar 
                </v-btn>
            </NuxtLink>
        </center>

    </div>
</template>
<script>
definePageMeta({
    layout: "default",
});

</script>