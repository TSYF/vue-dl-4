<template>
    <div class="form">
        <img alt="Vue logo" src="./assets/logo.png" />
        <h1>Lista de tareas</h1>
        <form @submit.prevent="submit()">
            <input
                type="text"
                placeholder="Ingrese tareas para hacer"
                v-model="input"
            />
            <button type="submit">Añadir</button>
        </form>
        <hr />

        <form-list :tareas="tareas" @eliminar-tarea="eliminarTarea" />
    </div>
</template>

<script>
import FormList from "./components/FormList.vue";
export default {
    components: { FormList },
    data() {
        return {
            input: undefined,
        };
    },
    methods: {
        submit() {
            this.tareas.push(this.input);
            return (this.input = undefined);
        },
        eliminarTarea(val) {
            this.tareas = this.tareas.filter((item, index) => index !== val);
        }
    },
    computed: {
      tareas() {
        return []
      }
    },
};
</script>

<style lang="scss">
.form {
    display: flex;
    flex-direction: column;
    align-items: center;

    ul {
        padding: 0;
    }
}
</style>
