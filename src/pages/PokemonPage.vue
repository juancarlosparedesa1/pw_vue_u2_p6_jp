<template>
    <div>
        <h1>Selecciona el Pokemon correcto</h1>
        <PokemonImagen :idPokemon="20" :mostrarPokemon="false" />
        <PokemonOpciones :pokemons="arreglo" />
    </div>
</template>

<script>
import PokemonImagen from '../components/PokemonImagen.vue'
import PokemonOpciones from '../components/PokemonOpciones.vue'

import obtenerPokemonsFachada from "../clientes/clientePokemonAPI"

export default {
    components: {
        PokemonImagen,
        PokemonOpciones,
        obtenerPokemonsFachada
    },
    methods: {
        async cargaInicial() {
            const vectorInicial = await obtenerPokemonsFachada(4);
            this.arreglo = vectorInicial;
        },
    },
    data() {
        return {
            arreglo: [],

        }
    },
    mounted() {
        this.cargaInicial();
    },
}
</script>

<style></style>
