<script setup lang="ts">
import { PropType } from 'vue';

defineProps({
  stats: {
    type: Object as PropType<IStats>,
    required: true,
  },
});

export interface IStats {
  active: number;
  done: number;
}
</script>

<template>
  <div>
    <footer class="app-footer">{{ stats.active }} more to do, {{ stats.done }} done</footer>
  </div>
</template>

<style scoped></style>
