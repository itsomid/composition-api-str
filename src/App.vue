<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ user.age }}</h3>
    <button @click="setAge">Set Age</button>
    <div>
      <input type="text" placeholder="First Name" v-model="firstName" />
      <input type="text" placeholder="Last Name" v-model="lastName" />
    </div>
  </section>
</template>

<script>
// eslint-disable-next-line
import { ref, reactive, computed } from "vue";
export default {
  setup() {
    //use for single value
    // eslint-disable-next-line
    let age = ref(31);
    const firstName = ref("Omid");
    const lastName = ref("Shabani");

    //use for object value
    let user = reactive({
      name: "OmidShabani",
      age: 31,
    });

    const userName = computed(function () {
      return firstName.value + " " + lastName.value;
    });

    function setNewData() {
      user.age = 33;
    }
    

    return {
      user: user,
      setAge: setNewData,
      userName,
      firstName,
      lastName,
    };
  },
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
