<template>
 <div v-show="showAddTask">
  <AddTask @add-task='addTask' @toggle-add-task="toggleAddTask" />
  </div>
  <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks= tasks />
    
</template>

<script>
import Tasks from '../components/Tasks.vue'
import AddTask from '../components/AddTask.vue'

export default {
    name: 'Home',
    props: {
        showAddTask: Boolean,
        toggleAddTask: Boolean
    },
    components: {
        Tasks,
        AddTask
    },
    data() {
        return {
            tasks: []
        }
    },
    methods: {
    async addTask(task){
      const res = await fetch('api/tasks', {
        method: 'POST',
        headers: {
          'Content-type': 'application/json',
          },
          body: JSON.stringify(task)
      }) 

    const data = await res.json()
    console.log(data);

      this.tasks = [...this.tasks, data]
    },
    toggleReminder(id){
      console.log(this.id);
    },
    async deleteTask(id) {
      if(confirm(`Are you sure?`)) {
        console.log(id);
        const res = await fetch(`api/tasks/${id}`, {
          method: 'DELETE'
        })
        res.status == 200 ? (this.tasks = this.tasks.filter((task => task.id !== id))) : alert('Task is not found')
      }
    },
    async fetchTasks() {
      const res = await fetch('api/tasks')
      const data = await res.json()
      return data
    },
    async fetchTask(id) {
      const res = await fetch(`api/tasks/${id}`)
      const data = await res.json()
      return data
    }
  },
  async created(){
    this.tasks = await this.fetchTasks()
  }

}
</script>