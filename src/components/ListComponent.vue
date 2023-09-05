<script setup>
import { ref } from 'vue';
import { reactive } from 'vue';

// give each todo a unique id
let id = 0;
let newTodo = ref('');

let todos = ref([
  { id: id++, text: 'Learn HTML' },
  { id: id++, text: 'Learn JavaScript' },
  { id: id++, text: 'Learn Vue' },
]);
let currentId = todos.value.length;

function checkArray(inputArray) {
  currentId = inputArray.value.length;
  console.log(`array length = ${currentId}`);
  inputArray.value.forEach(function (item, index) {
    console.groupCollapsed(`todos item ${index}`);
    console.log(`item = ${item.text}`);
    console.groupEnd('todos item');
  });
}

checkArray(todos);

function addTodo() {
  console.log(`newTodo input text = ${newTodo.value}`);

  if (newTodo.value !== '') {
    let newTodoElement = { id: currentId, text: newTodo.value };
    console.log(newTodoElement);
    todos.value.push(newTodoElement);
    checkArray(todos);
    newTodo.value = '';
  }
}

function removeTodo(todo) {
  console.log(`check delete`);
  console.log(`todo = ${todo.id}`);
  console.log(`todo = ${todo.text}`);

  let targetId = todo.id;

  todos.value = todos.value.filter(item => item.id != targetId)
}

</script>

<template>
  <h1>List component</h1>
  <div class="card">
    <h2>List Rendering</h2>

    <form @submit.prevent="addTodo">
      <input v-model="newTodo">
      <button>Add Todo</button>
    </form>

    <ul>
      <li v-for="todo in todos" :key="todo.id">
        {{ todo.text }}
        <button @click="removeTodo(todo)">X</button>
      </li>
    </ul>
  </div>
</template>

<style scoped></style>
