<script setup>
import {ref} from 'vue'

let newTask = ref('')
let tasks = ref([])

let addTask = ()=> {
    if (newTask.value.trim() != '' ) {
        tasks.value.push(newTask.value)
        newTask.value = ''
    }
}

let removeTask = (index)=> {
    tasks.value.splice(index, 1)
}

</script>
<template>
    <div class="todo-app">
        <h1>My To-Do App!</h1>
        <div class="task-input">
            <input v-model="newTask" @keyup.enter="addTask" placeholder="Add new task">
            <button @click="addTask" >Add Task</button>
        </div>

        <!--Renderring All the Task-->
        <ul class="task-list">
            <li v-for="(task,index) in tasks" :key="index" class="task-item">
                {{ task }}
            </li>
            <button @click="removeTask(index)" class="remove-btn">Remove Task</button>
        </ul>
    </div>
</template>

<style scoped>
.todo-app{
    padding: 20px;
    border: 2px solid #000;
    border-radius: 20px;
    margin: 50px auto;
    max-width: 1200px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    align-items: center;
    justify-content: center;
}

h1{
    text-align: center;
    justify-content: center;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    color: crimson;
  }

button{
    padding: 8px 12px;
    font-size: 14px;
    background-color: #4caf50;
    color: whitesmoke;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

.task-list{
    list-style: none;
    padding: 0;
}

.task-item{
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    margin: 8px 0;
    background-color: wheat;
    border: 1px solid black;
    border-radius: 4px;
}

.task-input{
    display: flex;
    gap: 10px;
}

input{
    flex: 1;
    padding: 8px;
    font-size: 18px;
}

button:hover{
    background: greenyellow;
    color: #000;
}

.remove-btn{
    padding: 6px 10px;
    font-size: 12px;
    background-color: #e74c3c;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}
.remove-btn:hover{
    background-color: #c0392b;
}

</style>