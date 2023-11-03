<template>
    <h3>Tasks to do</h3>
    <div>
        <input class="text-box" v-model="task" placeholder="Enter yout task"/>
        <button @click="addTask">Add</button>
    </div>
    <div>
        <ul>
            <li v-for="(elem, i) in tasks" :key="i">
                <input type="checkbox" v-model="elem.complete"/>
                <span :class="{ 'completed' : elem.complete}">{{ elem.text }}</span>
                <button class="delete-btn" @click="handleDelete(i)">Delete</button>
            </li>
        </ul>
    </div>
</template>

<script setup>
import { ref } from 'vue';

    const task = ref('');
    const tasks= ref([]);
    // ref:
    // It allows you to make a variable or object property reactive, 
    // meaning that any changes to the value will trigger reactivity 
    // and update the components that depend on it. 
    // This is commonly used for managing state in Vue components.
    const addTask = () =>{
        if(task.value.trim() !== ''){
            tasks.value.push({ text: task.value, complete: false});
            task.value = '';
        }
    }
    const handleDelete = (i) =>{
        tasks.value.splice(i, 1);
    }
</script>

<style scoped>
    h3{
        color: rgb(6, 124, 124);
        font-size: 25px;
    }
    .text-box{
        width: 380px;
        height: 30px;
    }
    ul{
        margin-top: 50px;
    }
    li{
        list-style-type: none;
        padding: 5px;
        display: flex;
    }
    button{
        margin: 8px;
        padding: 5px;
        color: rgb(6, 124, 124);
        border-color: rgb(6, 124, 124);
        border-radius: 5px;
        background-color: white;
    }
    .delete-btn{
        margin-left: auto;
    }
    span{
        padding: 5px;
        padding-top: 6px;
        padding-left: 12px;
        font-size: 20px;
    }
    .completed {
        text-decoration: line-through;
    }
</style>