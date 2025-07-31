<script setup>
defineProps({
  todo: Object
});
const emit = defineEmits(['remove']);
</script>

<template>
  <li>
    <input type="checkbox" v-model="todo.done">
    {{ todo.text }}
    <button @click="$emit('remove', todo)">X</button>
  </li>
</template>
