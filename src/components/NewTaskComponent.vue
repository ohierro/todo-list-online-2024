<script setup lang="ts">
import { ref } from 'vue';

const emits = defineEmits(['newTask'])
const taskName = ref('Inicial')

</script>

<template>
<div class="container">
  <div class="grow">
    <v-text-field
      label="Label"
      v-model="taskName"
    >
    </v-text-field>
  </div>
  <div>
    <v-btn @click="$emit('newTask', taskName)">Save</v-btn>
  </div>
</div>
</template>

<style scoped>
.container {
  display: flex;
}

.grow {
  flex-grow: 1;
}

</style>