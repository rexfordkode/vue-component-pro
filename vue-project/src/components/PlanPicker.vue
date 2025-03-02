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
const selectedCoffeePlan = ref()

function handleSelectedCoffeePlan(name: string) {
    selectedCoffeePlan.value = name
}
</script>
<template>

    <div ref="plansWrapper" class=" plans">
        <div class="selected-plan" v-if="selectedCoffeePlan">
            {{ selectedCoffeePlan }}
        </div>

        <CoffeePlan v-for="plan in plans" :name="plan.name" @click="handleSelectedCoffeePlan(plan.name)"
            :selected="plan === selectedCoffeePlan" :key="plan.name" />
    </div>
</template>


<style scoped>
.plans {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
    gap: 1.5rem;
    margin-top: 2rem;
}

.selected-plan {
    grid-column: 1 / -1;
    background-color: #f8f5f0;
    color: #ce946b;
    padding: 1rem 1.5rem;
    margin-bottom: 1rem;
    border-radius: 8px;
    font-weight: 600;
    font-size: 1.2rem;
    text-align: center;
    box-shadow: 0 2px 8px rgba(111, 78, 55, 0.1);
    border-left: 4px solid #6f4e37;
    animation: fadeIn 0.3s ease-in-out;
}

@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(-10px);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@media (max-width: 768px) {
    .plans {
        grid-template-columns: 1fr;
    }
}
</style>