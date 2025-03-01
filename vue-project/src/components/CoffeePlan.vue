<script setup lang="ts">
import { ref } from 'vue'
const props = defineProps<{
    name: {
        type: string, default: 'The Curious'
    }

}>()
const emit = defineEmits(['selected'])
const selected = ref(false)

function selectPlan() {
    selected.value = !selected.value
    emit('selected', props.name)
}
</script>
<template>
    <div @click="selectPlan" class="plan" :class="{ 'active-plan': selected }">
        <div class="description">
            <span cla ss="title"> {{ name }} </span>
        </div>
    </div>
</template>