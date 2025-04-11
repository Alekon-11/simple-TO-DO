<template>
    <ul class="todo-list">
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
import AppTodoItem from './AppTodoItem.vue'
import type { Todo } from '../interfaces/Todos'

interface Props {
    todos: Todo[]
}

defineProps<Props>()

const emit = defineEmits<{
    (e: 'toggleTodo', id: number): void
    (e: 'deleteTodo', id: number): void
}>()

const toggleTodo = (id: number) => {
    emit('toggleTodo', id)
}

const deleteTodo = (id: number) => {
    emit('deleteTodo', id)
}
</script>

<style scoped></style>
