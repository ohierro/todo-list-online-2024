<script setup lang="ts">
import NewTaskComponent from "@/components/NewTaskComponent.vue"
import TaskListComponent from "@/components/TaskListComponent.vue"
import { reactive } from "vue";
import type Task from "./core/task";

const tasks = reactive(new Array<Task>())

tasks.push(
  { id: 0, name: 'Create vue skeleton application', completed: true },
  { id: 1, name: 'Create the most awesome todo application', completed: false },
  { id: 2, name: 'Add some computed info', completed: false },
  { id: 3, name: 'Publish in github pages', completed: false },
)

function addTask(taskName: string) {
  tasks.push({
    id: tasks.length,
    name: taskName,
    completed: false
  })
}

function onTaskCompleted(id: number) {
  // console.log(`Tarea completa ${id}`);
  const task = tasks.filter(t => t.id === id)[0]
  task.completed = !task.completed
}
</script>

<template>
  <header>
    My Todos
  </header>

  <main>
    <NewTaskComponent
      @new-task="addTask"
    >
    </NewTaskComponent>
    <TaskListComponent
      :tasks="tasks"
      @task-completed="onTaskCompleted"
    ></TaskListComponent>
    <!-- NewTaskComponent -->
    <!-- TaskListComponent -->
    <!-- InfoTasksComponent -->

    <div>Tareas completas: {{ tasks.filter(t => t.completed).length }}</div>
  </main>
</template>

<style scoped>
main {
  display: flex;
  flex-direction: column;
  flex-grow: auto;
  height: 100%;
}
</style>
