<template>
    <div>
        <ul>
            <TodoItem v-for="todo in todos" :key="todo.id" :todo="todo"/>
        </ul>
    </div>
</template>

<script>
    import TodoItem from "./TodoItem";
    export default {
        name: "TodoList",
        props: ["todos"],
        components: {
            TodoItem
        }
    }
</script>

<style scoped>
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
    }
</style>