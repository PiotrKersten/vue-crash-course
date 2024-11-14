<!-- shorter way to use composition api -->
<script setup>
import { onMounted, ref } from 'vue';

const name = ref('John Doe');
const status = ref('active');
const tasks = ref(['t1', 't2', 't3', 't4']);
const newTask = ref('');
const link = ref('https://google.com');

const toggleStatus = () =>{
  if(status.value === 'active'){
    status.value = 'pending';
  } else if(status.value ==='pending'){
    status.value = 'inactive';
  }else{
    status.value = 'active';
  }
};

const addTask = ()=>{
  if(newTask.value.trim() !== '') {
    tasks.value.push(newTask.value);
    newTask.value = '';
  }
};

const deleteTask = (index) =>{
  tasks.value.splice(index, 1);
};

onMounted(async () => {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/todos');
    const data = await response.json();
    tasks.value = data.map((task) => task.title);
  }catch(error) {
    console.log('Error fething tasks');
  }

});

</script>

<template>
  <h1>{{name}}</h1>
  <p v-if="status==='active'">User's active</p>
  <p v-else-if="status==='pending'">Users's pending</p>
  <p v-else>User's inactive</p>

  <form @submit.prevent="addTask">
    <label for="newTask">Add Task </label>
    <input type="text" id="newTask" name="newTask" v-model="newTask" />
    <button type="submit">Submit</button>
  </form>

  <h3>Tasks:</h3>
  <ul>
    <li v-for="(task,index) in tasks" :key="task">
      <span>
        {{ task }}
      </span>
      <button @click="deleteTask(index)">x</button>
    </li>
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


