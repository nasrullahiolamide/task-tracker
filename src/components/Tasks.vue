<template>
    <div 
    :key="task.id"  
    v-for="task in tasks">

       <Task 
       @toggle-reminder="$emit('toggle-reminder', task.id)" 
       @delete-task="$emit('delete-task', task.id)" :task="task"
        />

    </div>

</template>



<script>
import Task from './Task'

export default {
    name: 'Tasks',
    props: {
        tasks: Array,
        reminder: Boolean
    },
    components: {
        Task
    },
    emits: [
        'toggle-reminder',
        'delete-task'
    ]
}
</script>

<style>
.task{
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer
}

.task.reminder{
    border-left: 5px solid green;
}

.task h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

</style>