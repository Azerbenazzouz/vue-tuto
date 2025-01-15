<script setup>
import { ref } from 'vue';

  const name = ref('Azer ben azzouz');
  const status = ref('active');
  const tasks = ref(['task 1', 'task 2', 'task 3']);

  const changeStatus = () => {
    if (status.value === 'active') {
      status.value = 'pending';
    } else if (status.value === 'pending') {
      status.value = 'inactive';
    } else {
      status.value = 'active';
    }
  }

</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <p v-else>User is not active</p>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks">
      {{ task }}
    </li>
  </ul>

  <br>
  
  <button @click="changeStatus">Change Status</button>

</template>