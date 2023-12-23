<script setup lang="ts">
import TodoHeader from './components/TodoHeader.vue';
import TodoFilters from './components/TodoFilters.vue';
import TodoItemList from './components/TodoItemList.vue';
import TodoAddTodo from './components/TodoAddTodo.vue';
import TodoFooter, { IStats } from './components/TodoFooter.vue';
import { computed, ref } from 'vue';
import { ITodo } from './types/Todo';
import { Filter } from './types/Filter';

interface State {
  todos: ITodo[];
  activeFilter: Filter;
}

const todos = ref<ITodo[]>([
  { id: 0, text: 'Learn the basics of vue', completed: true },
  { id: 1, text: 'Learn the basics of vue', completed: false },
  { id: 2, text: 'Learn the basics of vue', completed: false },
]);

const activeFilter = ref<Filter>('All');

const activeTodos = computed<ITodo[]>(() => {
  return todos.value.filter((todo) => !todo.completed);
});
const doneTodos = computed<ITodo[]>(() => {
  return todos.value.filter((todo) => todo.completed);
});

const filteredTodos = computed<ITodo[]>(() => {
  // switch (activeFilter.value) {
  //   case 'Active':
  //     return activeTodos.value;
  //   case 'Done':
  //     return doneTodos.value;
  //   case 'All':
  //   default:
  //     return todos.value;
  // }

  return {
    Active: activeTodos.value,
    Done: doneTodos.value,
    All: todos.value,
  }[activeFilter.value];
});

const stats = computed<IStats>(() => {
  return {
    active: activeTodos.value.length,
    done: doneTodos.value.length,
  };
});

const toggleTodo = (id: number) => {
  const targetTodo = todos.value.find((todo) => todo.id === id);
  if (targetTodo) {
    targetTodo.completed = !targetTodo.completed;
  }
};
const deleteTodo = (id: number) => {
  todos.value = todos.value.filter((todo) => todo.id !== id);
};
const addTodo = (todo: ITodo) => {
  if (todo.text) todos.value.push(todo);
};

const setFilter = (filter: Filter) => {
  activeFilter.value = filter;
};
</script>

<template>
  <div id="app">
    <TodoHeader />
    <TodoFilters :active-filter="activeFilter" @set-filter="setFilter" />

    <main class="app-main">
      <TodoItemList :todos="filteredTodos" @delete-todo="deleteTodo" @toggle-todo="toggleTodo" />
      <TodoAddTodo @add-todo="addTodo" />
    </main>

    <TodoFooter :stats="stats" />
  </div>
</template>

<style scoped></style>
