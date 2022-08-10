<template>
    <div class="todo" v-bind:class="{completed: todo.completed}">
        <div class="todo-body" >
            <input id="check_1" type="checkbox" 
                v-bind:checked="todo.completed ? 'checked': ''"
                v-on:change="checkTodo">
            {{todo.title}}
        </div>
        <div class="todo-actions">
            <button @click="$emit('delete-todo', todo.id)">Eliminar</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'TareaItem',
        props: ['todo'],
        methods: {
            checkTodo(){
                this.todo.completed = !this.todo.completed;
            }
        }
    }
</script>

<style scoped>
    .todo{
        border-bottom: solid 1px #ccc;
        padding: 10px;
        display: flex;
    }
    .todo:not(.completed):hover{
        background-color: #eee;
    }
    .completed{
        color: darkred;
        text-decoration: line-through;
        display: flex;
    }
    .completed .todo-body{
        text-decoration: line-through;
        font-size: 18px;
        display: flex;
        align-items: center;
    }
    .todo-body, .todo-actions{
        display: inline-block;
        vertical-align: top;
    }
    .todo-body{
        width: 100%;
        font-size: 18px;
        display: flex;
        align-items: center;
        cursor: pointer;
    }
    .todo-actions{
        float:right;
        display: flex;
        align-items: center;
    }
    button{
        border: none;
        border-radius: 3px;
        padding: 7px;
        background-color: #ccc;
        color: white;
        background-color: #da2020;
        cursor: pointer;
    }
    button:hover{
        background-color: #da2020;
        color: white;
        cursor: pointer;
    }
    #check_1{
        margin-right: 10px;
    } 
</style>