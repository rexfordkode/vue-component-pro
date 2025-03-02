<script setup lang="ts">
const props = defineProps({
    name: {
        type: String, default: 'The Curious', validator(value: string) { return value.startsWith('The') }
    },
    selected: {
        type: Boolean, default: false
    }
})

const emit = defineEmits({
    selected(payload: string) {
        return typeof payload === 'string'
    }
})
function selectedPlan() {
    emit('selected', props.name)
}
</script>
<template>
    <div @click="selectedPlan" class="plan" :class="{ 'active-plan': selected }">
        <div class="description">
            <span class="title"> {{ name }} </span>
        </div>
    </div>
</template>