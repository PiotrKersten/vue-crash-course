<!-- longer way to use composition api -->
<script>
import { ref } from 'vue';

  export default{
    setup () {
      const name = ref('John Doe');
      const status = ref('active');
      const tasks = ref(['t1', 't2', 't3']);
      const link = ref('https://google.com');

      const toggleStatus = () =>{
        if(status.value === 'active'){
          status.value = 'pending';
        } else if(status.value ==='pending'){
          status.value = 'inactive';
        }else{
          status.value = 'active';
        }
      }

      return {
        name,
        status,
        tasks,
        toggleStatus,
      };
    },
  };
</script>

<template>
  <h1>{{name}}</h1>
  <p v-if="status==='active'">User's active</p>
  <p v-else-if="status==='pending'">Users's pending</p>
  <p v-else>User's inactive</p>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <!-- <a v-bind:href="link">Click for google</a> -->
  <!-- SAME AS -->
  <a :href="link">Click for google</a>
  <br />
  <!-- <button v-on:click="toggleStatus">Change status</button> -->
  <!-- SAME AS -->
  <button @click="toggleStatus">Change status</button>
</template>

<style scoped>
h1 {
  color: aqua;
}

</style>

