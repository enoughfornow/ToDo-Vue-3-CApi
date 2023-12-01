<script setup lang="ts">
import TodoHeader from './components/TodoHeader.vue';
import TodoFilters from './components/TodoFilters.vue';
import TodoItemList from './components/TodoItemList.vue';
import TodoAddTodo from './components/TodoAddTodo.vue';
import TodoFooter from './components/TodoFooter.vue';
</script>

<template>
  <div id="app">
    <TodoHeader />
    <TodoFilters />

    <main class="app-main">
      <TodoItemList />
      <TodoAddTodo />
    </main>

    <TodoFooter />
  </div>
</template>

<style scoped></style>
