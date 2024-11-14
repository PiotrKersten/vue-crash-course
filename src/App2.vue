<script>
  export default{
    data(){
      return{
        name: 'John Doe',
        status: 'active',
        tasks: ['t1', 't2', 't3'],
        link: 'https://google.com',
      };
    },

    methods: {
      toggleStatus() {
        if(this.status === 'active'){
          this.status = 'pending';
        } else if(this.status ==='pending'){
          this.status = 'inactive';
        }else{
          this.status = 'active';
        }
      },
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


