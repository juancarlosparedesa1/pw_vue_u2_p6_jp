<template>
  <img src="./assets/logo.png" alt="No existe">
  <!--   <Contador titulo="Estudiante" :num="1" /> v-bind -->
  <Contador titulo="Estudiante" :num="-1" />
  <!--   <Contador titulo="Profesor" v-bind:num="5" /> v-bind -->
  <Contador titulo="Profesor" />
  <Contador v-bind:num="calcularValor()" />
</template>

<script>
import Contador from './components/Contador.vue'

export default {
  name: 'App',
  components: {
    Contador
  },
  methods: {
    calcularValor() {
      return 10 + 2;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
