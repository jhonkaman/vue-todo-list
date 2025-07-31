<script setup>
// Import Vue composition API and child components
import { ref, computed } from 'vue';
import TodoInput from './TodoInput.vue';
import TodoListDisplay from './TodoListDisplay.vue';
import TodoToggle from './TodoToggle.vue';

// Unique ID counter for todos
let id = 0;

// Reactive state to control hiding completed todos
const hideCompleted = ref(false);

// Reactive array of todo objects
const todos = ref([
  { id: id++, text: 'Learn HTML', done: true },
  { id: id++, text: 'Learn JavaScript', done: true },
  { id: id++, text: 'Learn Vue', done: false }
]);

// Computed property to filter todos based on hideCompleted
const visibleTodos = computed(() =>
  hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
);

// Add a new todo to the list
function addTodo(text) {
  todos.value.push({ id: id++, text, done: false });
}

// Remove a todo from the list
function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo);
}
</script>

<template>
  <h1>Vue Todo List</h1>
  <!-- Input component for adding new todos -->
  <TodoInput @add="addTodo" />
  <!-- Toggle component to show/hide completed todos -->
  <TodoToggle
    :hide-completed="hideCompleted"
    @toggle="hideCompleted = !hideCompleted"
  />
  <!-- Display component for showing the list of todos -->
  <TodoListDisplay :todos="visibleTodos" @remove="removeTodo" />
</template>
