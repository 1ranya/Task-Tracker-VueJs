<template>
    <div>
        <div v-for="task in tasks"  :key="task.id" class="task">
            <Task 
                @toggle-reminder="$emit('toggle-reminder', task.id)" 
                @delete-task="$emit('delete-task', task.id)"  :task = "task"/>
        </div>
    </div>
</template>

<script>
import Task from './Task'
export default {
    name: "Tasks", 
    props: {
        tasks:Array
    },
    components:{
        Task
    }, 
    methods:{
        
    }, 
    emits:['delete-task', 'toggle-reminder']
}
</script>

<style scoped>
.task{

}
</style>