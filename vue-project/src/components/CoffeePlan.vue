<script setup lang="ts">
const props = defineProps<{
    name: {
        type: string, default: 'The Curious'
    },
    selected: {
        type: boolean, default: false
    }

}>()

</script>
<template>
    <div class="plan" :class="{ 'active-plan': selected }">
        <div class="description">
            <span cla ss="title"> {{ name }} </span>
        </div>
    </div>
</template>