<template>
    <div>
      <ul v-if="checkTask" class="space-y-2">
        <TodoItem v-for="task in listOfTask" :key="task.id" :task="task" :deleteTask="deleteTask" />
      </ul>
      <div v-else>
        <p class="text-center">List of Task is Empty</p>
      </div>
    </div>
  </template>
  
  <script setup>
  
  import TodoItem from './TodoItem.vue';
  

  </script>
  