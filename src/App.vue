<template>
  <!-- <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ userAge }}</h3>
  </section> -->
  <user-app :first-name="firstName" :last-name="lastName"></user-app>
  <section class="container">
    <!-- <h2>{{ user.name }}</h2>
    <h3>{{ user.age }}</h3> -->
    <!-- <button @click="user.age++">+1 Age</button> -->
    <div>
      <button @click="setAges">+1 Age</button>
    </div>
    <div>{{ fullName }}</div>
    <!-- <input type="text" placeholder="First Name" @input="setFirstName" />
    <input type="text" placeholder="Last Name" @input="setLastName" /> -->
    <input type="text" placeholder="First Name" v-model="user.firstName" />
    <input type="text" placeholder="Last Name" ref="lastNameInput" />
    <button @click="setLastName">set Last Name</button>
  </section>
</template>

<script>
import UserApp from './component/UserApp';
// import { ref } from 'vue';  // ref can work with a string and a number and requires .value

import { reactive, computed, watch, ref } from 'vue'; // reactive works only with an object and doesn't require .value
export default {
  components: {
    UserApp
  },
  setup() {
    const user = reactive({
      name: 'Alexander',
      age: 35,
      firstName: '',
      lastName: ''
    });
    const userAge = ref(33);
    const lastNameInput = ref(null);
    const firstName = 'Alexander';
    const lastName = 'Tsyhan';

    const setLastName = function() {
      user.lastName = lastNameInput.value.value;
    };

    // function setFirstName(event) {
    //   user.firstName = event.target.value;
    // }

    // function setLastName(event) {
    //   user.lastName = event.target.value;
    // }

    // userAge is watched

    const fullName = computed(function() {
      return user.firstName + ' ' + user.lastName;
    });

    // setTimeout(() => {
    //   user.name = 'Alex';
    //   user.age++;
    // }, 2000);

    const setAges = function() {
      //   userAge.value++;
      user.age++;
      return user.age;
    };

    watch([setAges, fullName], function(newValues, oldValues) {
      console.log('old Value: ' + oldValues[0]);
      console.log('new Value: ' + newValues[0]);
    });

    return {
      user,
      setAges,
      userAge,
      //   setFirstName,
      //   setLastName,
      fullName,
      setLastName,
      lastNameInput,
      firstName,
      lastName
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
