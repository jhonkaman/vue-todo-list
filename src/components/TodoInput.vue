<script setup>
import { ref } from 'vue';

const emit = defineEmits(['add']);
const input = ref('');

function submit() {
  if (input.value.trim()) {
    emit('add', input.value);
    input.value = '';
  }
}
</script>

<template>
  <input v-model="input" @keyup.enter="submit">
  <button @click="submit">Add Todo</button>
</template>
