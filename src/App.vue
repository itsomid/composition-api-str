<template>
  <section class="container">
    <h2>{{ user.name }}</h2>
    <h3>{{ user.age }}</h3>
    <button @click="setAge">Set Age</button>
  </section>
</template>

<script>
// eslint-disable-next-line
import { ref, reactive } from 'vue'
export default {
  setup() {
    //use for single value
    // eslint-disable-next-line
    let age = ref(31)
    
    //use for object value
    let user = reactive({
      name: 'OmidShabani',
      age: 31
    });

    function setNewData(){
      user.age = 33
    }

    return { user: user, setAge: setNewData };
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
