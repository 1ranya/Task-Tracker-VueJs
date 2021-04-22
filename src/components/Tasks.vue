<template>
    <div>
        <div v-for="task in tasks"  :key="task.id" class="task">
            <Task :task = "task"/>
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
    }
}
</script>

<style scoped>
.task{
    background-color: rgb(220, 223, 224);
    width: 20rem;
    display: flex; 
    justify-content: space-between;
    align-items: center;
}
</style>