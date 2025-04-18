<template>
    <div id="app">
        <AppHeader />

        <AppFilters :active-filter="activeFilter" @switch-filter="switchFilter" />

        <main class="app-main">
            <AppTodoList :todos="filteredTodos" @delete-todo="deleteTodo" @toggle-todo="toggleTodo" />

            <AppAddTodo @create-todo-item="createTodoItem" />
        </main>

        <AppFooter :active-todos="activeTodos.length" :done-todos="doneTodos.length" />
    </div>
</template>

<script setup lang="ts">
import AppHeader from './components/AppHeader.vue'
import AppFilters from './components/AppFilters.vue'
import AppFooter from './components/AppFooter.vue'
import AppAddTodo from './components/AppAddTodo.vue'
import AppTodoList from './components/AppTodoList.vue'
import type { Todo } from './interfaces/Todos'
import { computed, ref } from 'vue'
import type { Filters } from './types/Filters'

const todos = ref<Todo[]>([
    { id: 0, text: 'Learn the basics of Vue', completed: false },
    { id: 1, text: 'Learn the basics of Typescript', completed: false },
    { id: 2, text: 'Subscribe to the channel', completed: false }
])
const activeFilter = ref<Filters>('All')

const activeTodos = computed(() => todos.value.filter((item: Todo) => !item.completed))
const doneTodos = computed(() => todos.value.filter((item: Todo) => item.completed))

const filteredTodos = computed(() => {
    switch (activeFilter.value) {
        case 'Active':
            return activeTodos.value
            break
        case 'Done':
            return doneTodos.value
            break
        case 'All':
        default:
            return todos.value
            break
    }
})

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

const createTodoItem = (todo: Todo) => {
    todos.value.push(todo)
}

const switchFilter = (filter: Filters) => {
    activeFilter.value = filter
}
</script>

<style scoped></style>
