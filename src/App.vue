<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ userAge }}</h3>
  </section>
  <section class="container">
    <h2>{{ user.name }}</h2>
    <h3>{{ user.age }}</h3>
  </section>
</template>

<script>
// import { ref } from 'vue';  // ref can work with a string and a number and requires .value

import { reactive, toRefs } from 'vue'; // reactive works only with an object and doesn't require .value
export default {
  //   data() {
  //     return {
  //       userName: 'Maximilian',
  //     };
  //   },
  setup() {
    // const uName = ref('Alexander');
    // const uAge = ref(36);

    // const user = ref({
    const user = reactive({
      name: 'Alexander',
      age: 35
    });

    const userRefs = toRefs(user);

    setTimeout(() => {
      //   uName.value = 'Alex';
      //   uAge.value++;
      //   user.value.name = 'Alex';
      //   user.value.age++;
      user.name = 'Alex';
      user.age++;
    }, 2000);

    return {
      //   userName: uName,
      //   userAge: uAge
      //   userName: user.value.name,
      //   userAge: user.value.age,
      user: user,
      userName: userRefs.name,
      userAge: userRefs.age
    };
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>
