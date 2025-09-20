<script setup lang="ts">
import { onMounted } from 'vue';

const IS_ENABLE_DARK_MODE: boolean = false

onMounted(() => {
    const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
    if (prefersDark && IS_ENABLE_DARK_MODE) {
        document.documentElement.classList.add('dark');
    } else {
        document.documentElement.classList = '';
    }
})
</script>
<template>
    <slot />
</template>