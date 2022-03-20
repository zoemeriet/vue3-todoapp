<template>
  <li class="todoitem--component">
    <label :for="index" class="todoitem--label">
      <input type="checkbox" :id="index" :checked="todo.done" @click="toggleDone(todo)">
      <span className="todoitem--checkmark"></span>
      <p :class="{ done: todo.done }">{{ todo.content }}</p>
    </label>
    <button @click="removeTodo(index)">Remove todo</button>
  </li>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  todo: Object,
  index: Number,
  toggleDone: Function,
  removeTodo: Function
})


</script>

<style lang="scss">
@import './assets/styles/base.scss';
.todoitem {
  &--component {
    input {
      position: absolute;
      opacity: 0;
      cursor: pointer;
      height: 0;
      width: 0;
    }
  }
  &--label {
    position: relative;
    display: flex;
    align-items: center;
    margin: 10px 0;
  }
  &--checkmark {
    position: relative;
    height: 20px;
    width: 20px;
    border: 2px solid $grey;
    border-radius: 50%;
    margin-right: 18px;
  }
}
</style>
