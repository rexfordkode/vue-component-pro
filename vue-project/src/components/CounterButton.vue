<script setup lang="ts">
import { ref } from 'vue'
const count = ref(0)
console.log(count)
</script>


<template>
    <button @click="$event => count++" class="counter-button">
        {{ count }}
    </button>
</template>