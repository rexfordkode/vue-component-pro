<script setup lang="ts">
import CounterButton from './components/CounterButton.vue'
import PlanPicker from './components/PlanPicker.vue'
import FancyButton from './components/FancyButton.vue'
import GithubCard from './components/GithubCard.vue'
import AppAlert from './components/AppAlert.vue'
import { ref } from 'vue'

const alerts = ref([{
  message: 'New software update available.',
  type: 'info'
}, {
  message: 'Your purchase has been confirm.',
  type: 'success'
}, {
  message: 'Warning: Invalid email address!.',
  type: 'warning'
}, {
  message: 'Error! Task failed successfully.',
  type: 'error'
}])

const usernames = ref(['rexfordkode', 'eodAmalitech', 'qambongo', 'ahmadawais', 'angiejones', "kunal-kushwaha"])




</script>

<template>

  <div class="p-5">

    <GithubCard v-for="username in usernames" :key="username" :username="username"></GithubCard>


    <PlanPicker />
    <!-- <CounterButton /> -->

    <AppAlert v-for="alert in alerts" :key="alert.message" :type="alert.type"
      @closed="alerts => alerts.filter(a => a.message !== alert.message)">
      {{ alert.message }}
    </AppAlert>
    <pre>{{ alerts }}</pre>


  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    plstyletems: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
