<template>
    <div id="main">
        <span class="titulo">{{ message }}</span>
        <br>
        <br>
        <label class="label"> Tarea: </label>
        <input class="input" type="text" v-model="tarea">
        <button @click="crearTarea">Crear</button>
        <p v-if="mostrar"> Su nombre es:{{tarea}}</p>
        <br>
        <br>
        <h2 class="h2">Lista</h2>
        <br>
        <br>
        <div class="container">
            <ul v-for="(tarea,index) in tareas" :key="index">

                <li> <input v-bind:value="index" @click="borrarTarea" type="checkbox">{{tarea.name}}</li>

            </ul>
        </div>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                message: 'Crea una nueva tarea',
                tarea: "",
                tareas: [],
                mostrar: false
            }
        },
        methods: {
            mostrarNombre: function () {
                this.mostrar = !this.mostrar;
            },
            crearTarea: function () {
                if (this.tarea !== "") {

                    this.tareas.push({
                        name: this.tarea
                    });
                }
                this.tarea = ""
            },
            borrarTarea: function (index) {
                this.tareas.splice(index, 1)
            }

        },
    }
</script>
<style>
    * {
        padding: 0;
        margin: 0;
        font-family: Verdana, Geneva, Tahoma, sans-serif
    }


    #main {
        padding: 4rem;
        text-align: center;
        font-size: 25px;
        font-family: 'Calibri', sans-serif;
        color: rgb(30, 29, 29);
        background: rgb(0, 181, 191);
        height: 100vh;
    }



    button {
        background: rgb(12, 71, 245);
        color: #fff;
        border: none;
        width: 80px;
        height: 30px;
        border-radius: 5px;
    }

    .input {
        width: 140px;
        height: 30px;
        border-radius: 5px;
        border: none;
    }

    .label {
        font-size: 25px;
    }

    .h2 {
        font-size: 20px;
    }

    .lista {
        font-size: 20px;
    }

    .container {
        width: 200px;
        margin: 0 auto;
        text-align: left;
        margin-left: 45%;
    }
</style>