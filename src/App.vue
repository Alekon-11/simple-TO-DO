<template>
    <div id="app">
        <AppHeader />

        <AppFilters />

        <main class="app-main">
            <AppTodoList />

            <AppAddTodo />
        </main>

        <AppFooter />
    </div>
</template>

<script setup lang="ts">
import AppHeader from './components/AppHeader.vue'
import AppFilters from './components/AppFilters.vue'
import AppFooter from './components/AppFooter.vue'
import AppAddTodo from './components/AppAddTodo.vue'
import AppTodoList from './components/AppTodoList.vue'
</script>

<style scoped></style>
