<script setup>

    const newTask = ref('');
    const tasks = ref([]);

    const addTask = () => {
        tasks.value.push(newTask.value);
        newTask.value = '';
    };
    
    const removeTask = (index) => {
        tasks.value.splice(index, 1);
    };


</script>

<template>
  <div>
    <h1>Todo List</h1>
    <form @submit.prevent="addTask">
      <input v-model="newTask" type="text" placeholder="Enter a todo" />
      <button type="submit">Add</button>
    </form>
    <ul>
        <div v-if="tasks.length < 10">
            <li v-for="(task, index) in tasks" :key="index">
                {{ task }}
            <button @click="removeTask(index)">Delete</button>
            </li>
        </div>
        <div v-else>
          <p>Trop de tâches ! 🧨🧨</p>
        </div>
    </ul>
  </div>
</template>