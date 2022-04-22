<template>
<div  class="container">
  <headerComponent @toggle-add-task= "toggleAddTask"  :showAddTask="showAddTask" />
  <div v-show="showAddTask">
  <AddTask @add-task='addTask' @toggle-add-task="toggleAddTask" />
  </div>
  <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks= tasks />
</div>
</template>

<script>
import headerComponent from './components/Header.vue'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'


export default {
  name: 'App',
  components: {
    headerComponent,
    Tasks,
    AddTask
  },
  data() {
    return{
      tasks: [],
      showAddTask: false
    }
  },
  methods: {
    toggleAddTask(){
      this.showAddTask = !this.showAddTask
    },
    addTask(task){
      this.tasks = [...this.tasks, task]
    },
    toggleReminder(id){
      console.log(this.id);
    },

    deleteTask(id) {
      if(confirm(`Are you sure?`)) {
        this.tasks = this.tasks.filter((task => task.id !== id))
      }
    }
  },
  created(){
    this.tasks = [
      {
        id: 1,
        task: 'Chicken fila',
        day: 'Oct 1, 1960',
        reminder: true
      },
      {
        id: 2,
        task: 'Eat tamru',
        day: 'Oct 30, 2020',
        reminder: false
      },
      {
        id: 3,
        task: 'Address public',
        day: 'Oct 1, 2022',
        reminder: true
      },
    ]
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
