<template>
    <li class="todo-item" :class="{ 'todo-item--done': todo.completed }" @click="toggleTodo">
        <div class="todo-item__status">
            <i class="bi bi-check2"></i>
        </div>
        <span class="todo-item__text">{{ todo.text }}</span>
        <button class="todo-item__remove-button" @click.stop="deleteTodo">
            <i class="bi bi-trash3"></i>
        </button>
    </li>
</template>

<script setup lang="ts">
import type { Todo } from '../interfaces/Todos'

interface Props {
    todo: Todo
}

const props = defineProps<Props>()
const emit = defineEmits<{
    (e: 'toggleTodo', id: number): void
    (e: 'deleteTodo', id: number): void
}>()

const toggleTodo = () => {
    emit('toggleTodo', props.todo.id)
}

const deleteTodo = () => {
    emit('deleteTodo', props.todo.id)
}
</script>

<style scoped></style>
