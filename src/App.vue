<template>
  <h1>Vue 3 Todo App</h1>
  <form @submit.prevent="addNewTodo">
    <label for="">New Todo</label>
    <input v-model="newTodo" name="newTodo" type="text">
    <button>Add New Todo</button>
  </form>
  <button @click="removeAllTodos()">Remove all</button>
  <button @click="markAllDone()">Mark all done</button>
  <ul>
    <TodoItem v-for="(todo, index) in todos" :todo="todo" :key="index" :index="index" :toggle-done="toggleDone" :remove-todo="removeTodo" />
  </ul>
</template>

<script setup>
import { ref } from 'vue';
import TodoItem from './components/TodoItem.vue';

const newTodo = ref('');
const todos = ref([]);

const addNewTodo = () => {
  todos.value.push({
    done: false,
    content: newTodo.value
  });
  newTodo.value = '';
}

const removeTodo = (index) => {
  todos.value.splice(index, 1);
}

const toggleDone = (todo) => {
  todo.done = !todo.done;
}

const markAllDone = () => {
  todos.value.forEach(todo => todo.done = true);
}

const removeAllTodos = () => {
  todos.value = [];
}
</script>

<style>
.done {
  text-decoration: line-through;
}
</style>
