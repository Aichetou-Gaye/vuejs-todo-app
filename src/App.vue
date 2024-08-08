<template>
  <div>
    <h1>Vue 3 Todo App</h1>
    <form @submit.prevent="addNewTodo">

      <label>New Todo</label>
      <input v-model="newTodo" name="newTodo">
      <button>Add New Todo</button>
    </form>
    <button @click="removeAll()">Remove All Todos</button>
    <button @click="markAllDone()">Mark All Done</button>
    <ul>
      <li v-for="(todo, index) in todos" :key="todo.id">
        <h3 :class="{done: todo.done}" @click="toggleDone(todo)" class="todo">{{ todo.content }}</h3>
        <button @click="removeTodo(index)" class="remove">Remove Todo</button>
      </li>
    </ul>

  </div>
</template>

<script setup>
import { ref } from 'vue';

const newTodo = ref('')
const todos = ref([])

function addNewTodo() {
  todos.value.push({
    id: Date.now(),
    done: false,
    content: newTodo.value,
  })
  newTodo.value = ''
}

function toggleDone(todo) {
  todo.done = !todo.done
}

function removeTodo(index) {
  todos.value.splice(index, 1)
}
function markAllDone() {
  todos.value.forEach((todo) => todo.done = true)
}

function removeAll() {
  todos.value = []
}
// return {
//  newTodo,
//   addNewTodo,
// }

</script>

<style scoped>
body {
  font-family: sans-serif;
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
  height: 6vh;
  border: none;
  border-radius: 5px;
  font-weight: 800;
  align-self: center;
  margin: 20px 0;
  cursor: pointer;
}

input, textarea, button, p, div, section,article, select {
  display: block;
  width: 100%;
  font-family: sans-serif;
  /* font-size: 1em;
  margin: 0.5em; */
}
.todo{
  cursor: pointer;
}
.done {
  text-decoration: line-through;
}
button:active{
  transform: scale(1.1);
}
</style>
