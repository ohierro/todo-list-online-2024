<script setup lang="ts">
import { ref } from 'vue';

defineEmits(['taskCompleted'])

const props = defineProps<{
  id: number,
  name: string,
  completed: boolean
}>()

const taskCompleted = ref(false)
taskCompleted.value = props.completed

</script>

<template>
<div>
  <v-checkbox
    v-model="taskCompleted"
    @click="$emit('taskCompleted', id)"
    >
  </v-checkbox>
  <div>{{ name }}</div>
  <v-btn color="error">remove</v-btn>
</div>
</template>

<style scoped>
div {
  display: flex;
}
</style>