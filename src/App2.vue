<script>
export default {
  data() {
    return {
      name: 'Azer ben azzouz',
      status: 'pending',
      tasks: [
        'Task 1',
        'Task 2',
        'Task 3'
      ],
      link: 'https://www.google.com'
    }
  },
  methods: {
    changeStatus() {
      if (this.status === 'active') {
        this.status = 'pending'
      } else if (this.status === 'pending') {
        this.status = 'inactive'
      } else {
        this.status = 'active'
      }
    }
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

  <a v-bind:href="link">Go To Google</a>
  <br>
  <a :href="link">Go To Google</a>
  <br>
  
  <button v-on:click="changeStatus">Change Status</button>
  <button @click="changeStatus">Change Status</button>

</template>