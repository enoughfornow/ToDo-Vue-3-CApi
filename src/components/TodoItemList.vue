<script setup lang="ts">
import { reactive } from 'vue';
import TodoItem from './TodoItem.vue';

const todos = reactive([
  { id: 0, text: 'Learn the basics of vue', completed: true },
  { id: 1, text: 'Learn the basics of vue', completed: false },
  { id: 2, text: 'Learn the basics of vue', completed: false }
]);
</script>

<template>
  <div>
    <ul class="todo-list">
      // TODO
      <TodoItem v-for="todo in todos" :todo="todo" />
    </ul>
  </div>
</template>

<style scoped></style>
