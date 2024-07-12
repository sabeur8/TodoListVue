<template>
    <div>
        <li class="task">
            <span :class="editClass">{{data}}</span>
            <button class="delete-btn" @click="handleDelete">🗑️</button>
            <button class="edit-btn" @click="handleComplete" >  ✏️</button>
        </li>
        
    </div>
</template>
<script>
    export default{
        data(){
            return{
               editClass : ''
            }
        },
        props : ['data' , 'deleteFnt'],
        methods : {
            handleDelete (){
                this.deleteFnt(this.data)
            },
            handleComplete (){
                this.editClass = 'task-completed'
            }
        }
        
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