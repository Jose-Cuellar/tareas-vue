<template>
    <div id="add-container">
        <form @submit="addTodo">
            <input id="add_tarea" placeholder="Crear nueva tarea" type="text" v-model="title">
        </form>
    </div>
</template>

<script>
import { uuid } from 'vue-uuid';

export default {
    name: 'TareaAdd',
    data(){
        return {
            title: ''
        }
    },
    methods:{
        addTodo(e){
            e.preventDefault();

            const newTodo = {
                id: uuid.v4(),
                title: this.title,
                completed: false
            };

            this.title = '';
            this.$emit('add-todo', newTodo);
        }
    }
}
</script>

<style scoped>
    #add-container{
        padding: 10px;
    }
    input{
        padding: 10px;
        outline: none;
        border: solid 1px #ccc;
        width: 100%;
    }
    ::placeholder {
        color: black;
    }
</style>