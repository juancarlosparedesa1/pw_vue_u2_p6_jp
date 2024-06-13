<template>
    <img v-if="img" v-bind:src="img" alt="no se pudo cargar">

    <div class="oscuro">
        <div class="pregunta-container">
            <input v-model="pregunta" type="text" placeholder="Hazme una pregunta">
            <p>Recuerda terminar la pregunta con el signo de interrogación(?)</p>
            <div class="respuesta">
                <h2>{{ pregunta }}</h2>
                <h1>{{ respuesta }}</h1>
            </div>
        </div>
    </div>
</template>

<script>
export default {

    data() {
        return {
            pregunta: null,
            respuesta: null,
            img: null
        }
    },
    watch: {
        pregunta(value, oldValue) {
            console.log({ value, oldValue })
            if (!value.includes('?')) {
                return;//salgase del observador
            }
            //Consumir el API para obtener la respuesta
            this.obtenerRespuesta();
        },
    },
    methods: {
        async obtenerRespuesta() {
            this.respuesta = "Pensando......."
            const data = await fetch('https://yesno.wtf/api').then(r => r.json())
            console.log(data);
            const { answer, forced, image } = data;
            console.log(answer);
            this.respuesta = answer;
            this.img = image;
            return data;
        },
        async prueba() {
            const data2 = await this.obtenerRespuesta();
        }
    },
}
</script>

<style>
img,
.oscuro {
    max-height: 100%;
    height: 100vh;
    max-width: 100%;
    width: 100vw;
    position: fixed;
    top: 0px;
    left: 0px;

}

.oscuro {
    background: rgba(0, 0, 0, .4);
    /* 0.0 full transparente, 1.0 full opaco*/

}

.pregunta-container {
    position: relative;

}

input {
    margin-top: 40px;
    width: 260px;
    padding: 10px 15px;
    border: none;
    border-radius: 5px;
}

input:focus {

    outline: none;
}

p,
h1,
h2 {
    color: white
}

p {
    font-size: 25px;
    margin-top: 0px;
}

.respuesta {
    margin-top: 100px;
}
</style>