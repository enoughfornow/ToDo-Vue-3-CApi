<script setup lang="ts">
import { ref } from 'vue';
import { ITodo } from '../types/Todo';

const emit = defineEmits<{
  (e: 'addTodo', todo: ITodo): void;
}>();

const addTodo = () => {
  emit('addTodo', { id: Date.now(), text: todoText.value, completed: false });
  todoText.value = '';
};

const IsVisible = ref(true);
const todoText = ref('');

const closeForm = () => (IsVisible.value = false);
const showForm = () => (IsVisible.value = true);
</script>

<template>
  <div>
    <section class="add-todo">
      <form v-if="IsVisible" @submit.prevent="addTodo" class="add-todo__form">
        <button @click="closeForm" class="close-button" type="button">
          <i class="bi bi-x"></i>
        </button>
        <div class="text-input text-input--focus">
          <input v-model="todoText" class="input" />
        </div>
        <button class="button button--filled">Add task</button>
      </form>
      <button v-else @click="showForm" class="add-todo__show-form-button">
        <i class="bi bi-plus-lg"></i>
      </button>
    </section>
  </div>
</template>

<style scoped></style>
