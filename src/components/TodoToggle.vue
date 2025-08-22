<script setup>
defineProps({
  hideCompleted: Boolean
});
const emit = defineEmits(['toggle']);
</script>

<template>
  <label>
    <input
      type="checkbox"
      :checked="hideCompleted"
      @change="$emit('toggle')"
    />
    Hide Completed
  </label>
</template>
