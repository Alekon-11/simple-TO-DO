<template>
    <aside class="app-filters">
        <section class="toggle-group">
            <button
                v-for="filter in filterList"
                class="button"
                :class="{ 'button--primary': activeFilter === filter }"
                @click="() => switchFilter(filter)"
            >
                {{ filter }}
            </button>
        </section>
    </aside>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import type { Filters } from '../types/Filters'

const filterList = ref<Filters[]>(['All', 'Active', 'Done'])
const emit = defineEmits<{
    (e: 'switchFilter', filter: Filters): void
}>()

interface Props {
    activeFilter: Filters
}

const switchFilter = (filter: Filters) => {
    emit('switchFilter', filter)
}

defineProps<Props>()
</script>

<style scoped></style>
