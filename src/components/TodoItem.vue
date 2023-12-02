<script setup lang="ts">
interface IProps {
  todo: {
    id: number;
    text: string;
    completed: boolean;
  };
}

defineProps<IProps>();
const emit = defineEmits<{
  (e: 'toggleTodo', id: number): void;
}>();
</script>
<template>
  <div>
    <li
      class="todo-item"
      :class="{ 'todo-item--done': todo.completed }"
      @click="emit('toggleTodo', todo.id)"
    >
      <div class="todo-item__status">
        <i class="bi bi-check2"></i>
      </div>
      <span class="todo-item__text">{{ todo.text }}</span>
      <button class="todo-item__remove-button">
        <i class="bi bi-trash3"></i>
      </button>
    </li>
  </div>
</template>

<style scoped></style>
