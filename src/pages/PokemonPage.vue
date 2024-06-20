<template>
    <div>
        <h1>Selecciona el Pokemon correcto</h1>
        <PokemonImagen />
        <PokemonOpciones />
    </div>
</template>

<script>
import PokemonImagen from '../components/PokemonImagen.vue'
import PokemonOpciones from '../components/PokemonOpciones.vue'

export default {
    components: {
        PokemonImagen,
        PokemonOpciones
    }
}
</script>

<style></style>
