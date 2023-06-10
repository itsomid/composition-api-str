<template>
  <h2>{{ userName }}</h2>
  <h3>{{ age }}</h3>
</template>
<script>
import { computed, inject } from "vue";
export default {
  setup() {
  
    const userData = inject('userData')

    const userName = computed(function(){
        return userData.firstName + ' ' + userData.lastName
    })
    const age = computed(function(){
        return userData.age
    })
    // const age = inject('userAge')
    // const firstName = inject('firstName')
    // const lastName = inject('lastName')
    // const userName = computed(function () {
    //   return firstName.value + " " + lastName.value;
    // });

    return {
      userName,
      age
    };
  },
};
</script>
