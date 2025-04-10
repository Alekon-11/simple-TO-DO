<template>
    <ul class="todo-list">
        <!-- <AppTodoItem v-for="todo in todos" :todo="{ id: todo.id, text: todo.text, completed: todo.completed }" /> -->
        <AppTodoItem
            @delete-todo="deleteTodo"
            @toggle-todo="toggleTodo"
            v-for="todo in todos"
            :key="todo.id"
            :todo="todo"
        />
    </ul>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import AppTodoItem from './AppTodoItem.vue'
import type { Todo } from '../interfaces/Todos'

const todos = ref<Todo[]>([
    { id: 0, text: 'Learn the basics of Vue', completed: true },
    { id: 1, text: 'Learn the basics of Typescript', completed: false },
    { id: 2, text: 'Subscribe to the channel', completed: false }
])

const toggleTodo = (id: number) => {
    const targetTodo = todos.value.find((item: Todo) => item.id === id)

    if (targetTodo) {
        targetTodo.completed = !targetTodo.completed
    }
}

const deleteTodo = (id: number) => {
    const newTodos = todos.value.filter((item: Todo) => item.id !== id)
    todos.value = newTodos
}
</script>

<style scoped></style>
