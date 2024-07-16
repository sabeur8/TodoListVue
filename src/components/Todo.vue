<template>
    <div>
        <li class="task">
            <span :class="editClass">{{props.data}}</span>
            <button class="delete-btn" @click="handleDelete">🗑️</button>
        </li>
        <button class="edit-btn" @click="handleComplete" >  ✏️</button>
    </div>
</template>
<script setup>

import { ref } from 'vue'
    
const props = defineProps (['data' , 'deleteFnt'])
const editClass = ref('')

function handleComplete (){
    editClass.value = 'task-completed'
}
function handleDelete (){
    props.deleteFnt(props.data)
}
</script>

<style>
.task {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #ccc;
}
.task-actions {
    display: flex;
    align-items: center;
}
.delete-btn {
    background-color: #f44336;
  color: white;
  padding: 5px 10px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.task-completed  {
    text-decoration: line-through;
    color: #999;
}
</style>