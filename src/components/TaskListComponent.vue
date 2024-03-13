<script setup lang="ts">
import type Task from '@/core/task';
import TaskListItem from '@/components/TaskListItem.vue';

defineEmits(['taskCompleted'])

const props = defineProps<{
  tasks: Task[]
}>()
</script>

<template>
  <TaskListItem
    v-for="task in tasks"
    :key="task.id"
    :id="task.id"
    :name="task.name"
    :completed="task.completed"
    @task-completed="$emit('taskCompleted', task.id)"
  >
  </TaskListItem>
</template>