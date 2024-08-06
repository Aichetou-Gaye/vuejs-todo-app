<template>
  <div>
    <h1>Vue 3 Todo App</h1>
    <form @submit.prevent ="addNewTodo">

      <label>New Todo</label>
      <input v-model="newTodo" name="newTodo">
      <button>Add New Todo</button>
    </form>
    <h2>{{ newTodo }}</h2>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const newTodo = ref('')
function addNewTodo() {
  console.log(newTodo.value)
}

// return {
//   addNewTodo,

// }

</script>

<style scoped>
body{
  font-family : sans-serif;
  padding-top: 1em;
  padding-bottom: 1em;
  font-size: 2em;
  width: 80%;
  margin: 0 auto;
}
h1 {
  color: rgb(5, 100, 100);
  font-weight: bolder;
  text-align: center;
  font-size: 3em;
  margin-bottom: 30px;
}
form {
  display: flex;
  flex-direction: column;
  gap: 10px;
}
label {
  font-size: 20px;
  font-weight: 600;
}
input {
  box-shadow: 1px 2px 2px 1px rgb(5, 100, 100);
  height: 8vh;
  border: none;
  border-radius: 10px
}
button {
  background-color: rgb(5, 100, 100);
  color: white;
  height: 5vh;
  width: 40%;
  border: none;
  border-radius: 5px;
  font-size: 1em;
  font-weight: 800;
  font-family : sans-serif;
  align-self: center;
  margin-top: 15px;
  cursor: pointer;
}
</style>
