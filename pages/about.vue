<script  setup >

    const task = ref([]);
    const newTask = ref('');

    const addTask = () => {
        if(newTask.value !== ""){
            task.value.push(newTask.value);
            newTask.value = "";
        }
    }

    const removeTask = (index) => {
        task.value.splice(index,1);
    }

</script>

<template>
    <div>
        <h1>My todo</h1>
        <form @submit.prevent="addTask">
            <input type="text" v-model="newTask" placeholder="enter your todo"/>
            <button type="submit">add</button>
        </form>

        <ul>
            <li v-for="(task, index) in task" :key="index">
                {{ task }}
                <button @click="removeTask(index)">Delete</button>
            </li>
        </ul>

    </div>
</template>