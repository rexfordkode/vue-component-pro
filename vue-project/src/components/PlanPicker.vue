<script setup lang="ts">
import { ref } from 'vue'
import CoffeePlan from './CoffeePlan.vue'
const plans = ref([
    { name: 'The Curious' },
    { name: 'The Explorer' },
    { name: 'The Addict' },
    { name: 'The Single' },
    { name: 'The Hacker' }
])
const selectedCoffeePlan = ref('')

function handleSelectedPlan(name: string) {
    selectedCoffeePlan.value = name
}
</script>
<template>
    <div class="plans">
        {{ selectedCoffeePlan }}
        <CoffeePlan v-for="plan in plans" :name="plan.name" @selected="$event => handleSelectedPlan(plan.name)"
            :key="plan.name" />
    </div>
</template>