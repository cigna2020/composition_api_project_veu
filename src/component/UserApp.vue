<template>
  <section class="container">
    <h2>{{ firstName }}</h2>
    <h3>{{ lastName }}</h3>
    <h2>{{ fullName }}</h2>
  </section>
</template>

<script>
import { computed } from 'vue';

export default {
  props: ['firstName', 'lastName'],
  //   computed: {
  //     fullName() {
  //       return this.firstName + ' ' + this.lastName;
  //     }
  //   }
  setup(props) {
    const fullName = computed(function() {
      return props.firstName + ' ' + props.lastName;
    });

    return { fullName };
  }
};
</script>
