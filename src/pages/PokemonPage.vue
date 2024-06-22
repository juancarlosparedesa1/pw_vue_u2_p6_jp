<template>
    <div>
        <h1 v-if="!pokemonCorrecto">Por favor espere...</h1>
        <div v-else>
            <h1>Selecciona el Pokémon correcto</h1>
            <PokemonImagen :idPokemon="pokemonCorrecto.id" :mostrarPokemon="mostrar" />
            <PokemonOpciones :pokemons="arreglo" @seleccionPokemon="revisarRespuesta($event)" />
            <div v-if="mostrarMensaje">
                <p>Pokémon Correcto: {{ pokemonCorrecto.nombre }}</p>
                <p>¡Correcto!</p>
            </div>
        </div>
    </div>
</template>
  
<script>
import PokemonImagen from '../components/PokemonImagen.vue'
import PokemonOpciones from '../components/PokemonOpciones.vue'
import obtenerPokemonsFachada from "../clientes/clientePokemonAPI"

export default {
    components: {
        PokemonImagen,
        PokemonOpciones
    },
    data() {
        return {
            arreglo: [],
            pokemonCorrecto: null,
            mostrar: false,
            mostrarMensaje: false
        }
    },
    methods: {
        async cargaInicial() {
            const vectorInicial = await obtenerPokemonsFachada(7);
            this.arreglo = vectorInicial;
            const indice = Math.floor(Math.random() * 7);
            this.pokemonCorrecto = this.arreglo[indice];
        },
        revisarRespuesta(dato) {
            if (dato.ident === this.pokemonCorrecto.id) {
                this.mostrar = true;
                this.mostrarMensaje = true;
            } else {
                console.log('¡Incorrecto!');
            }
        }
    },
    mounted() {
        this.cargaInicial();
    }
}
</script>
  
<style></style>
  