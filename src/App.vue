<template>
  <section class="container">
    <user-data :first-name="firstName" :last-name="lastName" :age="age"></user-data>
    <button @click="setAge">Set Age</button>
    <div>
      <input type="text" placeholder="First Name" v-model="firstName" />
      <input type="text" placeholder="Last Name" ref="lastNameInput" />
      <button @click="setLastName">set last name</button>
    </div>
  </section>
</template>

<script>
import { ref, watch } from "vue";
import UserData from "./components/USerData.vue";
export default {
  components: {
    UserData,
  },
  setup() {
    //use for single value

    let uAge = ref(31);
    const firstName = ref("Omid");
    const lastName = ref("");
    const lastNameInput = ref(null);
    //use for object value
    // let user = reactive({
    //   name: "OmidShabani",
    //   age: 31,
    // });

    watch([uAge], function (newValues, oldValues) {
      console.log(oldValues[0]);
      console.log(newValues[0]);
    });

    function setNewData() {
      uAge.value = 33;
    }

    function setLastName() {
      lastName.value = lastNameInput.value.value;
    }

    return {
      age: uAge,
      setAge: setNewData,
      firstName,
      lastName,
      lastNameInput,
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
