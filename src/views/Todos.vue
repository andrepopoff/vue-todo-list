<template>
    <div>
        <h2>Todo application</h2>
        <router-link to="/">Home</router-link>
        <AddTodo @add-todo="addTodo"/>
        <hr>
        <Loader v-if="loading" />
        <TodoList v-else-if="todos.length" :todos="todos" @remove-todo="removeTodo"/>
        <p v-else>No todos!</p>
    </div>
</template>

<script>
    import TodoList from "@/components/TodoList";
    import AddTodo from "@/components/AddTodo";
    import Loader from "@/components/Loader";
    export default {
        name: 'App',
        data() {
            return {
                todos: [],
                loading: true
            }
        },
        components: {
            TodoList, AddTodo, Loader
        },
        mounted() {
            fetch('https://jsonplaceholder.typicode.com/todos?_limit=5')
                .then(response => response.json())
                .then(json => {
                    this.todos = json;
                    this.loading = false
                })
        },
        methods: {
            removeTodo(id) {
                this.todos = this.todos.filter(todo => todo.id !== id)
            },
            addTodo(todo) {
                this.todos.push(todo)
            }
        }
    }
</script>

<style scoped>

</style>