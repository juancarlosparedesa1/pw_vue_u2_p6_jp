<template>
    <div class="pokemon-container">
        <img v-show="mostrar"
            src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/1.svg"
            alt="No se puede mostrar">
        <img v-show="!mostrar" class="oculta-pokemon"
            src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/1.svg"
            alt="No se puede mostrar">
    </div>
</template>

<script>
export default {
    data() {
        return {
            mostrar: false,
        };
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
    right: 35%;
}

.pokemon-container {
    height: 200px;
}
</style>