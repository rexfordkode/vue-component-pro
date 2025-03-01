<script setup lang="ts">
import { ref } from 'vue'
const props = defineProps({
    username: {
        type: String,
        required: true,
        default: 'rexfordkode'
    }
})
const users = ref({})

fetch(`https://api.github.com/users/${props.username}`)
    .then((response) => response.json())
    .then((data) => {
        users.value = data
    })
    .catch((error) => {
        console.error(error)
    })

</script>
<template>

    <div v-if="users" class=" m-5 shadow-xl card card-side bg-base-100  ">
        <figure>
            <img :src="users.avatar_url" alt="Github Users" />
        </figure>
        <div class="card-body">
            <h2 class="card-title">{{ users.name }}</h2>
            <p>
                <strong>Followers:</strong>{{ users.followers }}
                <strong>Followers:</strong>{{ users.following }}
            </p>
            <div class="card-actions justify-end">
                <a :href="users.html_url" target="_blank" class=" btn btn-primary">View Profile</a>
            </div>
        </div>
    </div>

</template>