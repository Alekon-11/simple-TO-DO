<template>
    <footer class="app-footer">{{ activeTodos }} more to do, {{ doneTodos }} done</footer>
</template>

<script setup lang="ts">
interface Props {
    doneTodos: number
    activeTodos: number
}

defineProps<Props>()
</script>

<style scoped></style>
