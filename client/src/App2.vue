<script>//options
export default {
  data() {
    return {
      name: 'Vue.js',
      status: "active",
      tasks: ["task1", "task2"],
      link: "http://www.google.com"
    }
  },
  methods: {
    changeStatus() {
      if (this.status == "active") {
        this.status = "pending";
      } else if (this.status == "pending") {
        this.status = "inactive";
      } else {
        this.status = "active";
      }
    }
  }
}
</script>
<template>
  <h1>{{ name }}</h1>
  <h2 v-if="status === 'active'">{{ "is active" }}</h2>
  <h2 v-else-if="status === 'pending'">{{ "is pending" }}</h2>
  <h2 v-else>{{ "is inactive" }}</h2>
  <ul>
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>
  <a :href="link">Google</a>
  <!-- <button v-on:click="changeStatus">Change Status</button> -->
  <button @click="changeStatus">Change Status</button>
</template>
