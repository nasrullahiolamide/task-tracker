<template>
    <header>
        <h1>
            {{title}}
        </h1>
        <Button v-show="homePage"
        @toggle-add-task="$emit('toggle-add-task')" class="btn" 
        :text="showAddTask ? 'Close' : 'Add Task'"
        :color="showAddTask ? 'red' : 'green' " />
    </header>
</template>


<script>
import Button from './Button'

export default {
    name: 'headerComponent',
    props: {
        title: {
            type: String,
            default: 'Task Tracker'
        },
        showAddTask: Boolean
    },
    computed: {
        homePage() {
            if(this.$route.path === '/' ){
                return true
            } else {
                return false
            }
        }
    },
    components: {
        Button
    },
}
</script>

<style >
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>