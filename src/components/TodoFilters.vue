<script setup lang="ts">
import { PropType, ref } from 'vue';
import { Filter } from '../types/Filter';

const emit = defineEmits<{
  (e: 'setFilter', filter: Filter): void;
}>();

defineProps({
  activeFilter: {
    type: String as PropType<Filter>,
    required: true,
  },
});

interface State {
  filters: Filter[];
}

const filters = ref<Filter[]>(['All', 'Active', 'Done']);

const setFilter = (filter: Filter) => {
  emit('setFilter', filter);
};
</script>

<template>
  <div>
    <aside class="app-filters">
      <section class="toggle-group">
        <button
          v-for="filter in filters"
          :key="filter"
          @click="setFilter(filter)"
          class="button"
          :class="{ 'button--primary': activeFilter === filter }"
        >
          {{ filter }}
        </button>
      </section>
    </aside>
  </div>
</template>

<style scoped></style>
