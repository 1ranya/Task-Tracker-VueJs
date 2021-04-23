<template>
    <div 
        @dblclick="$emit('toggle-reminder', task.id)" 
        :class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>{{ task.text }}
            <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
        </h3>
        <p>{{ task.day }}</p>
    </div>
</template>

<script>
export default {
    name:"Task", 
    props:{
        task: Object
    }, 
    methods:{
    
    }
}
</script>

<style scoped>
    .fas{
        color: rgb(167, 33, 33);
        cursor: pointer;
    }
    .task {
        background: #f4f4f4;
        margin: 5px;
        padding: 10px 20px;
        cursor: pointer;
    }
    .task h3{
        display: flex; 
        align-items: center;
        justify-content: space-between;
    }
    .task.reminder {
        border-left: 5px solid green;
    }

</style>