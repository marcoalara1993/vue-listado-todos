<template>
    <div id="agregar-container">
        <form v-on:submit="agregarTodo">
            <input type="text" v-model="title">
        </form>
    </div>
</template>

<script>
import { uuid } from "vue-uuid";

export default {
    name: "TodoAgregar",
    data(){
        return {
            title: ""
        }
    },
    methods: {
        agregarTodo(event) {
            event.preventDefault();

            const nuevoTodo = {
                id: uuid.v4(),
                title: this.title,
                completed: false
            };

            this.title = "";
            this.$emit('agregar-todo' , nuevoTodo)
            
        }
    }
}
</script>

<style scoped>

    #agregar-container {
        padding: 10px;
    }

    input {
        padding: 10px;
        outline: none;
        border: 2px solid green;
        width: 100%;
    }


</style>