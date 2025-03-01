<script setup lang="ts">
import { ref } from 'vue'
const hover = ref(true)
</script>

<template>
    <button @mouseenter="$event => hover = true" @mouseleave="$event => hover = false" :class="{ 'hover': hover }"
        class="fancy-button">
        <slot name="icon" hover="hover" random="hello"></slot>
        <slot>Click Me</slot>

    </button>


</template>
