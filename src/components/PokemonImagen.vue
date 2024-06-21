<template>
    <div class="pokemon-container">
        <img v-show="mostrarPokemon" :src="imagenFuente" alt="No se puede mostrar">
        <img v-show="!mostrarPokemon" class="oculta-pokemon" :src="imagenFuente" alt="No se puede mostrar">
    </div>
</template>

<script>
export default {
    data() {
        return {
            mostrar: false,

        };
    },
    props: {
        idPokemon: {
            type: Number,
            required: true,
        },
        mostrarPokemon: {
            type: Boolean,
            required: true,
            default: false,
        },
    },
    computed: {
        imagenFuente() {
            return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.idPokemon}.svg`
        }
    }
}
</script>

<style scoped>
.oculta-pokemon {
    filter: brightness(0);
}

img {
    height: 200px;
    width: 200px;
    position: absolute;
    right: 40%;
}

.pokemon-container {
    height: 200px;
}
</style>