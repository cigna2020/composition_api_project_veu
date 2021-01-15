<template>
  <h2>My Course Goal</h2>
  <!-- Task 1: Output your main course goal with help of the composition API -->
  <!-- Don't hardcode it into the template, instead hardcode it into the JS code -->
  <h3>OUTPUT COURSE GOAL</h3>
  <ul class="container" v-if="isGoal.isGoal">
    <li v-for="goal in goalData" :key="goal">{{ goal }}</li>
  </ul>
  <!-- Task 2: Toggle (show/ hide) the goal with help of the button  -->
  <button @click="toggleGoal">Toggle Goal</button>
  <!-- Task 3: Manage data in three ways -->
  <!-- => Separate refs -->
  <!-- => Ref Object -->
  <!-- => Reactive Object -->
  <!-- Task 4: Also solve the assignment with the Options API -->
</template>

<script>
import { reactive } from 'vue';
export default {
  setup() {
    const goalData = reactive({
      goal1: 'Learn Vue.js',
      goal2: 'Became an expert in Vue.js',
      goal3: 'Learn React'
    });
    const isGoal = reactive({
      isGoal: false
    });

    function toggleGoal() {
      isGoal.isGoal = !isGoal.isGoal;
      console.log(isGoal.isGoal);
    }

    return {
      goalData: goalData,
      isGoal: isGoal,
      toggleGoal: toggleGoal
    };
  }
};
</script>

<style>
html {
  font-family: sans-serif;
}
body {
  margin: 3rem;
  text-align: center;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}

li {
  list-style: none;
  text-align: left;
  margin-top: 5px;
  font-size: 20px;
}
</style>
