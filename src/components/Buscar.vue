<template>
    <div id="buscador">
        <input type="text" v-model="query" v-on:input="$emit('cambiar-query', query)">
    </div>
</template>

<script>
export default {
    name: "Buscar",
    data(){
        return {
            query: ''
        }
    }
}
</script>

<style scoped>
    #buscador {
        width: 600px;
        margin: 0 auto;
    }

    input {
        padding: 10px;
        width: 100%;
        outline: none;
    }
</style>