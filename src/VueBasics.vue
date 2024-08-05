<script setup>
import { onMounted, ref } from "vue";

const name = ref("John Doe");
const status = ref(true);
const tasks = ref(["Task One", "Task Two", "Task Three"]);
const link = ref("https://google.com");

const newTask = ref("asfafafa");

const toggleStatus = () => {
  status.value = !status.value;
};

const addTask = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};

const deleteTask = (index) => {
  tasks.value.splice(index, 1);
};

onMounted(async () => {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/todos");
    const data = await response.json();
    tasks.value = data.map((task) => task.title);
  } catch (error) {
    console.log(error);
  }
});
</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status">User is active</p>
  <p v-else>User is inactive</p>

  <form action="" @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" v-model="newTask" id="newTask" name="newTask" />
    <button type="submit">Submit</button>
  </form>

  <h3>Tasks :</h3>
  <ul>
    <li v-for="(task, index) in tasks" :key="index">
      <span>{{ task }}</span>
      <button @click="deleteTask(index)">Delete</button>
    </li>
  </ul>
  <a :href="link">Google</a>

  <button @click="toggleStatus">Change status</button>
</template>

<style></style>
