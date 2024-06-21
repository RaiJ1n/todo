<template>
  <div class="app-background p-4">
    <h1 class="text-center text-2xl font-bold mb-4">Todo Vue</h1>
    <p class="mb-4">Number of Tasks: {{ listOfTask.length }}</p>
    <ul class="space-y-2">
      <todolist :listOfTask="listOfTask" :checkTask="checkTask"  />
    </ul>
    <div class="flex py-6 space-x-2">
      <input v-model="taskInput" type="text" class="border border-green-800 p-2 rounded flex-grow">
      <button @click="addTask" class="bg-green-500 text-white px-4 py-2 rounded">Add Task</button>
    </div>
  </div>
</template>

<script setup>
import { computed, ref } from 'vue';
import TodoList from './components/TodoList.vue';

const taskInput = ref('');

const listOfTask = ref([]);

const addTask = () => {
  if (taskInput.value.trim() !== '') {
    const taskData = {
      id: Date.now(),
      name: taskInput.value,
      isCompleted: false
    };
    listOfTask.value.push(taskData);
    taskInput.value = '';
  }
};

const checkTask = computed(() => {
  return listOfTask.value.length > 0;
});

const deleteTask = (id) => {
  listOfTask.value = listOfTask.value.filter((task) => task.id !== id);
};
</script>
