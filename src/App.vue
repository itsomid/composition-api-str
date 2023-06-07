<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ user.age }}</h3>
    <button @click="setAge">Set Age</button>
    <div>
      <input type="text" placeholder="First Name" @input="setFirstName" />
      <input type="text" placeholder="Last Name" @input="setLastName" />
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
    function setFirstName(event) {
      console.log(event.target.value);
      firstName.value = event.target.value;
    }
    function setLastName(event) {
      lastName.value = event.target.value;
    }

    return {
      user: user,
      setAge: setNewData,
      userName,
      setFirstName,
      setLastName,
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
