<template>
    <button :style="{ background : color }" class="primary btn"> 
        {{ text }}
    </button>
</template>

<script>
export default {
    name: 'Button', 
    props:{
        text: String, 
        color: String
    }
}
</script>

<style scoped>

</style>