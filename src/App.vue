<template>
  <section class="container">
    <user-data></user-data>
    <button @click="setAge">Set Age</button>
    <div>
      <input type="text" placeholder="First Name" v-model="fName" />
      <input type="text" placeholder="Last Name" ref="lastNameInput" />
      <button @click="setLastName">set last name</button>
    </div>
  </section>
</template>

<script>
import { ref, watch, provide, toRef } from "vue";
import UserData from "./components/USerData.vue";
export default {
  components: {
    UserData,
  },
  setup() {
    //use for single value

    let uAge = ref(31);
    const fName = ref("omidd")
    const lastNameInput = ref(null);

    const userData = ref({
      firstName: fName,
      lastName: "Shabani",
      age: 30
    })
    //use for object value
    // let user = reactive({
    //   name: "OmidShabani",
    //   age: 31,
    // });

    // provide("userAge", uAge);
    // provide("firstName", firstName);
    // provide("lastName", lastName);
    provide("userData", userData);

    watch([uAge], function (newValues, oldValues) {
      console.log(oldValues[0]);
      console.log(newValues[0]);
    });

    const setNewData = ()=> {
      userData.value.age = 33;
    }

    const setLastName = () => {
      userData.value.lastName = lastNameInput.value.value;
    };

    return {
      setAge: setNewData,
      fName,
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
