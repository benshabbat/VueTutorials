<script setup>//compositions
import { ref ,onMounted} from 'vue';
const name = ref('Vue.js');
const status = ref('active');
const tasks = ref(["task1", "task2"]);
const link = ref("http://www.google.com");
const newTask = ref("");

const changeStatus = () => {
  if (status.value == "active") {
    status.value = "pending";
  } else if (status.value == "pending") {
    status.value = "inactive";
  } else {
    status.value = "active";
  }
}

function addTask() {
  if (newTask.value.trim() === "") return;
  tasks.value.push(newTask.value);
  newTask.value = "";

}
function deleteTask(id) {
  tasks.value.splice(id, 1);
}
onMounted(async() => {
 try{
    const res = await fetch('http://jsonplaceholder.typicode.com/todos');
    const data = await res.json();
    tasks.value = data.map((task) => task.title);
  } catch (err) {
    console.log(err);
 }
})

</script>
<template>
  <h1>{{ name }}</h1>
  <h2 v-if="status === 'active'">{{ "is active" }}</h2>
  <h2 v-else-if="status === 'pending'">{{ "is pending" }}</h2>
  <h2 v-else>{{ "is inactive" }}</h2>
  <form @submit.prevent="addTask">
    <label for="newTask">New Task</label>
    <input type="text" id="newTask" name="newTask" v-model="newTask">
    <button type="submit">Add Task</button>

  </form>
  <ul>
    <li v-for="(task,index) in tasks" :key="task"><span>

      {{ task }}
    </span>
    <button @click="deleteTask(index)">Delete</button>
  </li>
  </ul>
  <a :href="link">Google</a>
  <!-- <button v-on:click="changeStatus">Change Status</button> -->
  <button @click="changeStatus">Change Status</button>
</template>
