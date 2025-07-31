<script setup>
import TodoItem from './TodoItem.vue';

defineProps({
  todos: Array
});
const emit = defineEmits(['remove']);
</script>

<template>
  <ul>
    <TodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
      @remove="(todo) => emit('remove', todo)"
    />
  </ul>
</template>
