<script setup lang="ts">
import { ref } from 'vue';
import TodoItem from './TodoItem.vue';

const todo = ref({ id: 0, text: 'Learn the basics of vue', completed: true });
</script>

<template>
  <div>
    <ul class="todo-list">
      // TODO
      <TodoItem :v-for="todo in todo" :todo="todo" /> 
    </ul>
  </div>
</template>

<style scoped></style>
