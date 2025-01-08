<script setup>
import { ref,onMounted } from "vue";

const name = ref("Mahmoud");
const status = ref("active");
const tasks = ref(["task one", "task two", "task three"]);
const newTask = ref("");

// نوع الحاله المطلوبه
const toggleStatus = () => {
  if (status.value === "active") {
    status.value = "pending";
  } else if (status.value === "pending") {
    /*  comp API methods with if*/
    status.value = "inactive";
  } else {
    status.value = "active";
  }
};

// اضافهnew task
const addTask = () => {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    newTask.value = "";
  }
};

// مسح task

const deleteTask = (index) => {
  tasks.value.splice(index,1);
 
};

onMounted(async() => {
  try {
    const response = await fetch ('https://jsonplaceholder.typicode.com/todos');
    const data =await response.json();
    tasks.value = data.map((task)=>task.title);
  } catch (error) {
    console.log('error fetshing tasks');
  }
});


</script>

<template>
  <h1>{{ name }}</h1>
  <p v-if="status === 'active'">User is active</p>
  <p v-else-if="status === 'pending'">User is pending</p>
  <!-- optional API if condations-->
  <p v-else>User is inactive</p>

  <!-- تكوين form-->
  <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <input type="text" id="newTask" name="newTtask" v-model="newTask" />
    <button type="submit">submit</button>
  </form>

  <h3>tasks:</h3>
  <ul>
    <li v-for="(tasks, index) in tasks" :key="tasks">
      <span>
        {{ tasks }}
      </span>

      <!--زرار المسح-->
      <button @click="deleteTask(index)">X</button>
    </li>
  </ul>
  <!-- الزرار-->
  <button @:click="toggleStatus">change status</button>
</template>
