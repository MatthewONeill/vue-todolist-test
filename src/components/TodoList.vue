<template>
    <input type="text" class="border border-black" v-model="todoText">
    <button class="border border-black ml-6" v-on:click="addTodo">Test</button>

    <ul v-if="todos.length">
        <Todo 
            v-for="todo in todos" 
            :key="todo.id"
            :todo="todo"
            @remove="removeTodo"
        />
    </ul>
    <p v-else>
        Nothing here.
    </p>
    
</template>


<script>
import Todo from './Todo.vue'

let todoId = 1;

export default {
    components: {
        Todo
    },
    name: 'TodoList',
    props: {
    },

    data () {
        return {
            todos: [
                {
                    id: 0,
                    text: "test"
                }
            ],
            todoText: ''
        }
    },

    methods: {
        addTodo: function () {
            this.todos.push({
                id: todoId++,
                text: this.todoText
            })
        },
        removeTodo (id) {
            this.todos = this.todos.filter(todo => {
                return todo.id !== id
            });
        }
    }
}
</script>

<style>

</style>