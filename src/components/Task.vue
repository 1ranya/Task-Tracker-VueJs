<template>
    <div>
        <h3>{{ task.text }}
            <i class="fa fa-time"></i>
        </h3>
        <h4>{{ task.day }}</h4>
    </div>
</template>

<script>
export default {
    name:"Task", 
    props:{
        task: Object
    }
}
</script>

<style scoped>

</style>