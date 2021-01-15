<template>
  <!-- <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ userAge }}</h3>
  </section> -->
  <section class="container">
    <h2>{{ user.name }}</h2>
    <h3>{{ user.age }}</h3>
    <!-- <button @click="user.age++">+1 Age</button> -->
    <div>
      <button @click="setAge">+1 Age</button>
    </div>
    <div>{{ fullName }}</div>
    <input type="text" placeholder="First Name" @input="setFirstName" />
    <input type="text" placeholder="Last Name" @input="setLastName" />
  </section>
</template>

<script>
// import { ref } from 'vue';  // ref can work with a string and a number and requires .value

import { reactive, computed } from 'vue'; // reactive works only with an object and doesn't require .value
export default {
  setup() {
    const user = reactive({
      name: 'Alexander',
      age: 35,
      firstName: '',
      lastName: ''
    });

    function setFirstName(event) {
      user.firstName = event.target.value;
    }

    function setLastName(event) {
      user.lastName = event.target.value;
    }

    const fullName = computed(function() {
      return user.firstName + ' ' + user.lastName;
    });

    setTimeout(() => {
      user.name = 'Alex';
      user.age++;
    }, 2000);

    function setAge() {
      user.age++;
    }

    return {
      user,
      setAge,
      setFirstName,
      setLastName,
      fullName
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
