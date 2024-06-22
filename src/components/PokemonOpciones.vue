<template>
    <div class="opciones-container">

        <ul>
            <li v-for="pokemon in pokemons" :key="pokemon.id"
                @click="$emit('seleccionPokemon', { ident: pokemon.id, nomb: pokemon.nombre, test: 'esto es una prueba', test2: test3 })">
                {{ pokemon.nombre }}
            </li>

        </ul>
    </div>
</template>

<script>
export default {
    props: {
        pokemons: {
            type: Array,
            required: true,
        }
    },
    data() {
        return {
            test3: 'segunda Prueba'
        }
    }
}
</script>

<style>
ul {
    list-style-type: none;
}

li {
    border: 1px solid black;
    border-radius: 5px;
    margin-bottom: 10px;
    width: 250px;
    background: white;
    cursor: pointer;
}

li:hover {
    background-color: rgba(0, 0, 0, 0.05);
}

.opciones-container {
    display: flex;
    justify-content: center;
}
</style>