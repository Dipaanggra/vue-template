<script setup>
import { ref } from 'vue';
import HelloWorld from './components/HelloWorld.vue'
// import TheWelcome from './components/TheWelcome.vue'
import axios from 'axios';
const form = ref({
  email: null,
  password: null
})
const submit = (() => {
  axios.post(`${import.meta.env.VITE_BASE_URL}/login`,
    form.value)
    .then(function (response) {
      console.log(response.data);
    })
    .catch(function (error) {
      console.log(error);
    });
})
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <form @submit.prevent="submit()">
      <input v-model="form.email" type="text" name="email">
      <br>
      <input v-model="form.password" type="password" name="password">
      <br>
      <button>Submit</button>
    </form>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
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
}
</style>
