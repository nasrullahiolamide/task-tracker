<template>
<div 
@dblclick="$emit('toggle-reminder', task.id)" 
:class="[ task.reminder ? 'reminder' : '', task]"
>
   <h3> {{task.task}} <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i> </h3>
   <p>{{task.day}}</p> 

</div>
</template>

<script>
import Button from './Button'
export default {
    name: 'Task',
    components: {
        Button
    },
    props: {
        task: Object
    },
    emits: ['toggle-reminder', 'delete-task']
}
</script>

<style>
.fas {
  color: red;
}
</style>