<template>
    <div className="todo-container">
      <h1> ToDo List <span>📝</span> </h1>

      <template v-for=" todo in todos" :key="todo.id" >

        <Todo :data="todo" :deleteFnt="handlDelete"/>
            
      </template>
      <div class="input-section">

      <input   type='text' id='task-input' placeholder='Add your task' v-model="newTodo" />
      <button id='add-task-btn' @click="handleAdd" > + </button>
      </div>

    </div>
</template>

<script>
import { ref } from 'vue'

import Todo from './Todo.vue'
    
export default{
        setup(){
            const todos = ref(['haircut', 'mearn javaScript', 'watch movie'])
            const newTodo = ref('')

            function handleAdd(){
                
                todos.value.push(newTodo.value)
            }
            function handlDelete (item) {
                console.log('delete')
                todos.value = todos.value.filter(
                    (element) => (item != element )
                )
            }
            
            return{
                handleAdd , handlDelete , todos , newTodo
            }
        },
        components : {
            Todo
        }
    }
</script>


<style>
body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 500%;
    margin: 0;
    background-color: #6cc3eb;
}

.todo-container {
    background: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    width: 300px;
}

h1 {
    text-align: center;
    margin: 0 0 20px;
}

.input-section {
    display: flex;
    align-items: center;
}

#task-input {
    flex: 1;
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    margin-right: 10px;
    margin-top:10px ;
}

#add-task-btn {
    background: #28a745;
    color: white;
    border: none;
    border-radius: 50%;
    width: 30px;
    height: 30px;
    font-size: 20px;
    cursor: pointer;
    margin-top: 10px;
}

#message {
    text-align: center;
    color: green;
    margin: 10px 0;
}

ul {
    list-style: none;
    padding: 0;
    margin: 0;
}


.task-actions button {
    background: none;
    border: none;
    cursor: pointer;
    font-size: 16px;
    margin-left: 10px;
}

.task-actions {
    background-color: #f44336;
  color: white;
  padding: 5px 10px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
</style>