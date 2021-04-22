<template>
    <div class="header">
        <h1>{{ title }}</h1>
        <Button text="Add" color="blue"/>
        <Button text="Remove" color="red"/>
        <Button text="Update" color="green"/>
    </div>
</template>

<script>
import Button from './Button'
export default {
    name: 'Header', 
    props:{
        title:String
    },
    components:{
        Button
    }
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