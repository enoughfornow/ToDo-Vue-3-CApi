<script setup lang="ts">
import { ITodo } from '../types/Todo';
import TodoItem from './TodoItem.vue';
import { PropType } from 'vue';

const emit = defineEmits<{
  (e: 'toggleTodo', id: number): void;
  (e: 'deleteTodo', id: number): void;
}>();

defineProps({
  todos: {
    type: Array as PropType<ITodo[]>,
  },
});

const toggleTodo = (id: number) => emit('toggleTodo', id);
const deleteTodo = (id: number) => emit('deleteTodo', id);
</script>

<template>
  <div>
    <ul class="todo-list">
      <TodoItem
        v-for="todo in todos"
        :todo="todo"
        @toggle-todo="toggleTodo"
        @delete-todo="deleteTodo"
      />
    </ul>
  </div>
</template>

<style scoped></style>
