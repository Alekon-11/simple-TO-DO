<template>
    <section class="add-todo">
        <form v-if="isOpenForm" class="add-todo__form" @submit.prevent="createTodoItem">
            <button class="close-button" type="button" @click="closeForm">
                <i class="bi bi-x"></i>
            </button>
            <div class="text-input text-input--focus">
                <input v-model="todoItemText" class="input" />
            </div>
            <button class="button button--filled">Add task</button>
        </form>
        <button v-else class="add-todo__show-form-button" @click="openForm">
            <i class="bi bi-plus-lg"></i>
        </button>
    </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import type { Todo } from '../interfaces/Todos'

const isOpenForm = ref<boolean>(false)
const todoItemText = ref<string>('')
const emit = defineEmits<{
    (e: 'createTodoItem', todo: Todo): void
}>()

const createTodoItem = () => {
    emit('createTodoItem', { id: Date.now(), text: todoItemText.value, completed: false })
    todoItemText.value = ''
}

const openForm = () => {
    isOpenForm.value = true
}
const closeForm = () => {
    isOpenForm.value = false
}
</script>

<style scoped></style>
