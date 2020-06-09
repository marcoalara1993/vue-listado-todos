<template>
    <div>
        <div v-bind:key="todo.id" v-for="todo in todoslista">
            <TodoItem v-bind:todo="todo" v-on:borrar-todo="$emit('borrar-todo', todo.id)" />
        </div>
    </div>
</template>

<script>
import TodoItem from "./TodoItem"

    export default {
        name: 'Todos',
        props: ['todoslista'],
        components: {TodoItem}
        
    }

</script>

<style></style>