<template>
  <div>
    <div id="header">
      <Search v-on:query-change="querySearch" />
    </div>

    <div id="main-container">
      <h2 id="title">Lista de tareas</h2>
      <TodoAdd v-on:add-todo="addTodo"/>
      <Todos v-bind:todoslist="copyTodos" v-on:delete-todo="deleteTodo" />
    </div>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Search from './components/Search';
import Todos from './components/Tareas';
import TodoAdd from './components/TareaAdd';

export default {
  name: 'App',
  components: {
    Todos, TodoAdd, Search
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id != id);
      this.copyTodos = [...this.todos];
    },
    addTodo(todo){
      this.todos.push(todo);
      this.copyTodos = [...this.todos];
    },
    querySearch(query){
      if(query.trim() === ''){
        this.copyTodos = [...this.todos];
      }else{
        const temp = this.todos.filter(todo =>{
          return todo.title.includes(query)
        });

        this.copyTodos = [...temp];
      }
    }
  },
  data(){
    return {
      todos: [
        {
          id: 0,
          title:  'Tarea pendiente',
          completed: false
        },
        {
          id: 1,
          title:  'Tarea completada',
          completed: true
        }
      ],
      copyTodos: []
    }
  },
  created(){
    this.copyTodos = [...this.todos];
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
    max-width: 1000px;
    margin: 25px auto auto auto;
  }
  html {
    background: linear-gradient(rgba(0, 0, 0, 0.4), rgba(0, 0, 0, 0.4)), url("http://1.bp.blogspot.com/-LoKTRPDCID8/UuvrxGJDnJI/AAAAAAAAPec/bhlsZ2_ltXw/s1600/FONDO%252BPERGAMINO%252BANTIGUO2.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
    background-attachment: fixed;
  }
  #main-container{
    border: solid 1px #ccc;
    width: auto;
    margin: auto;
  }
  #header{
    padding-bottom: 10px;
  }
  h2{
    padding: 0 10px;
  }
  #title{
    text-align: center;
    color: white;
  }
</style>
