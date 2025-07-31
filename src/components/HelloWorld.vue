<script setup>
// Import Vue composition API functions
import { ref, computed } from 'vue';

// Unique ID counter for todos
let id = 0;

// Reactive state for new todo input
const newTodo = ref('');

// Reactive state to control hiding completed todos
const hideCompleted = ref(false);

// Reactive array of todo objects
const todos = ref([
  { id: id++, text: 'Learn HTML', done: true },
  { id: id++, text: 'Learn JavaScript', done: true },
  { id: id++, text: 'Learn Vue', done: false }
]);

// Computed property to filter todos based on hideCompleted
const visibleTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})

// Add a new todo to the list
function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value });
  newTodo.value = '';
}

// Remove a todo from the list
function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <!-- Input for new todo -->
  <input v-model="newTodo">
  <button @click="addTodo">Add Todo</button>

  <!-- Checkbox to toggle hiding completed todos -->
  <label>
    <input type="checkbox" v-model="hideCompleted">
    Hide completed
  </label>

  <!-- List of visible todos -->
  <ul>
    <li v-for="todo in visibleTodos" :key="todo.id">
      <!-- Checkbox to mark todo as done/undone -->
      <input type="checkbox" v-model="todo.done">
      {{ todo.text }}
      <!-- Button to remove todo -->
      <button @click="removeTodo(todo)">X</button>
    </li>
  </ul>
</template>
