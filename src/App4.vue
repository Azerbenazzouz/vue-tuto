<script setup>
import { ref } from 'vue';

  const name = ref('Azer ben azzouz');
  const status = ref('active');
  const tasks = ref(['task 1', 'task 2', 'task 3']);
  const newTask = ref('');

  const changeStatus = () => {
    if (status.value === 'active') {
      status.value = 'pending';
    } else if (status.value === 'pending') {
      status.value = 'inactive';
    } else {
      status.value = 'active';
    }
  }

  const addTask = () => {
    if(newTask.value.trim() !== '') {
      tasks.value.push(newTask.value);
      newTask.value = '';
    } else {
      alert('Task cannot be empty');
    }
  }

  const deleteTask = (index) => {
    tasks.value.splice(index, 1);
  }
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is not active</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task </label>
    <input type="text" id="newTask" v-model="newTask">
    <button type="submit">Add</button>
  </form>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task, index) in tasks">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">X</button>
    </li>
  </ul>

  <br>
  
  <button @click="changeStatus">Change Status</button>

</template>