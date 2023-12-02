<script setup lang="ts">
import { ref } from 'vue';
import TodoItem from './TodoItem.vue';

const todos = ref([
  { id: 0, text: 'Learn the basics of vue', completed: true },
  { id: 1, text: 'Learn the basics of vue', completed: false },
  { id: 2, text: 'Learn the basics of vue', completed: false },
]);

const toggleTodo = (id: number) => {
  console.log(id);

  todos.value = todos.value.map((todo) => ({
    ...todo,
    completed: todo.id === id,
  }));
};
</script>

<template>
  <div>
    <ul class="todo-list">
      <TodoItem v-for="todo in todos" :todo="todo" @toggle-todo="toggleTodo" />
    </ul>
  </div>
</template>

<style scoped></style>
