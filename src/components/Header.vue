<template>
    <div class="header">
        <h1>{{ title }}</h1>
        <Button @btn-click="$emit('show-add-task')" 
                :text="showAddTaskVar ? 'Close' : 'Add Task'" 
                :color="showAddTaskVar ? 'red' : 'blue'"/>
        <!-- <Button text="Remove" color="red"/>
        <Button text="Update" color="green"/> -->   
    </div>
</template>

<script>
import Button from './Button'
export default {
    name: 'Header', 
    props:{
        title:String, 
        showAddTaskVar:Boolean,
    },
    components:{
        Button
    }, 
    emits:['show-add-task']
}
</script>

<style scoped>
    header{
        display: flex; 
        justify-content: space-between;
        align-items: center;
        margin-bottom: 2rem;
    }
</style>