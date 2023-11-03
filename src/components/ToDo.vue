<template>
    <h3>Task to do</h3>
    <input v-model="task" placeholder="Enter yout task"/>
    <button @click="addTask">Add</button>
    <div>
        <ul>
            <li v-for="(elem, i) in tasks" :key="i">
                <input type="checkbox" v-model="elem.complete"/>
                {{ elem.text }}
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
</script>

<style scoped>
    h3{
        color: rgb(6, 124, 124);
    }
</style>