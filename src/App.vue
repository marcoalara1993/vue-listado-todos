<template>
  <div>
    <div id="header">
      <Buscar v-on:cambiar-query="buscarQuery" />
    </div>

    <div id="main-container">
      <h2>Cosas por hacer</h2>
      <TodoAgregar v-on:agregar-todo="agregarTodo"/>
      <Todos v-bind:todoslista="copiarTodos" v-on:borrar-todo="borrarTodo" />
    </div>
  </div>
</template>

<script>

import Buscar from './components/Buscar';
import Todos from './components/Todos';
import TodoAgregar from './components/TodoAgregar';

export default {
  name: 'App',
  components: {
    Todos, TodoAgregar, Buscar
    
  },
  methods: {
    borrarTodo(id) {
      this.todos = this.todos.filter(todo => todo.id != id);
      this.copiarTodos = [...this.todos];
    },
    agregarTodo(todo){
      this.todos.push(todo);
      this.copiarTodos = [...this.todos];
    },
    buscarQuery(query){
      if(query.trim() === '') {
        this.copiarTodos = [...this.todos];
      } 
      else {
        const filtrado = this.todos.filter(todo => {
          return todo.title.includes(query)
        });
        this.copiarTodos = [...filtrado];
      }
    }
  },
  
  data(){
    return {
      todos: [
        {
          id: 0,
          title:  'Lavar la ropa',
          completed: false
        },
        {
         id: 1,
         title: 'Hacer el mercado',
         completed: true
       },
       {
         id: 2,
         title: 'Estudiar Vue-JS',
         completed: false
       },
       {
         id: 3,
         title: 'Jugar videojuegos',
         completed: true
       }
      ],
      copiarTodos: []
    }
  },
  created(){
    this.copiarTodos = [...this.todos];
  }
}
</script>

<style>
  *{
    box-sizing: border-box;
  }
  body{
    font-family: Arial, Helvetica, sans-serif;
    font-size: 1.5em;
    padding: 0;
    margin: 0;
  }
  #main-container{
    border: solid 1px #ccc;
    width: 600px;
    margin: 100px auto;
  }
  #header{
    background: black;
    padding: 10px;
  }
  h2{
    padding: 0 10px;
  }
</style>