<template>
    <div id="search-container">
        <input id="seach" type="text" placeholder="Buscar una tarea" v-model="query" v-on:input="$emit('query-change', query)">
    </div>
</template>

<script>
export default {
    name: 'Search',
    data(){
        return {
            query: ''
        }
    }
}
</script>

<style scoped>
    #search-container{
        width: auto;
        margin: 0 auto;
    }
    input{
        padding: 10px;
        width: 100%;
        outline: none;
        border: none;
    }
    ::placeholder {
        color: black;
    }
</style>