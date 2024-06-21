<template>
    <div class="flex justify-between items-center p-2 rounded mb-2"
         :class="{ 'bg-green-400 text-white': task.isCompleted, 'bg-red-600 text-white': !task.isCompleted }">
      <div>{{ task.name }}</div>
      <div class="flex items-center">
        <input type="checkbox" v-model="task.isCompleted" class="mr-2">
        <button @click="deleteTask(task.id)" class="bg-red-600 px-2 py-1 rounded ml-2 text-white" v-if="task.isCompleted">Remove</button>
      </div>
    </div>
  </template>
  
  <script setup>
  import { defineProps } from 'vue';
  
  const props = defineProps({
    task: Object,
    
  });
  </script>
  