<template>
    <ul class="todo-list">
        <AppTodoItem :word="test" />
    </ul>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import AppTodoItem from './AppTodoItem.vue'

const test = ref('f')
</script>

<style scoped></style>
