<script setup lang="ts">
interface IProps {
  todo: {
    id: number;
    text: string;
    completed: boolean;
  };
}

const emit = defineEmits<{
  (e: 'toggleTodo', id: number): void;
  (e: 'deleteTodo', id: number): void;
}>();

defineProps<IProps>();
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
      <button @click.stop="emit('deleteTodo', todo.id)" class="todo-item__remove-button">
        <i class="bi bi-trash3"></i>
      </button>
    </li>
  </div>
</template>

<style scoped></style>
