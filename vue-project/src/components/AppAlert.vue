<script setup lang="ts">
import IconError from './icons/IconError.vue'
import IconInfo from './icons/IconInfo.vue'
import IconSuccess from './icons/IconSuccess.vue'
import IconWarning from './icons/IconWarning.vue'

import { computed, ref } from 'vue'
const closed = ref(false)

const emit = defineEmits(['closed'])
function close() {
    closed.value = true
    emit('closed')
}

const props = defineProps({
    type: {
        type: String,
        default: 'alert-info'
    },
})

const alertType = computed(() => {
    return {
        info: 'alert-info',
        success: 'alert-success',
        warning: 'alert-warning',
        error: 'alert-error'
    }[props.type]
})

const icons = computed(() => {
    return {
        info: IconInfo,
        success: IconSuccess,
        warning: IconWarning,
        error: IconError
    }[props.type]
})



</script>
<template>
    <div v-if="!closed" role="alert" :class="`alert ${alertType}`">

        <component :is="icons">
        </component>

        <span>
            <slot></slot>
        </span>
        <button @click="close">x</button>

    </div>

</template>