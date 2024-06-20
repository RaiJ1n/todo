<template>
  <div class="app-background">
    <h1 class="text-center text-2xl font-bold mb-4">Todo Vue</h1>
    <p class="mb-4">Number of Tasks: {{ listOfTask.length }}</p>
    <ul>
      <div v-if="checkTask">
        <li v-for="task in listOfTask" :key="task.id" class="flex justify-between items-center p-2 rounded mb-2"
          :class="{ 'bg-blue-600 text-white': task.isCompleted, 'bg-red-600 text-black': !task.isCompleted }">
          <div>{{ task.name }}</div>
          <div class="flex items-center">
            <input type="checkbox" v-model="task.isCompleted" class="mr-2">
            <button v-on:click="deleteTask(task.id)" class="bg-gray-200 px-2 py-1 rounded ml-2" v-if="task.isCompleted">Remove</button>
          </div>
        </li>
      </div>
      <div v-else>
        <p class="text-center">List of Task is Empty</p>
      </div>
    </ul>
    <div class="flex py-6 space-x-2">
      <input v-model="taskInput" type="text" class="border border-green-800 p-2 rounded flex-grow">
      <button @click="addTask" class="bg-green-500 text-white px-4 py-2 rounded">Add Task</button>
    </div>
  </div>
</template>

<script setup>
import { computed, ref } from 'vue';

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