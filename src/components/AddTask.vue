<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label for="">Task</label>
            <input v-model="text" type="text" name="text" id="" placeholder="Add Task"/>
        </div>
        <div class="form-control">
            <label for="">Day and Time</label>
            <input v-model="day" type="text" name="day" id="" placeholder="Add Day and Time"/>
        </div>  
        <div class="form-control form-control-check">
            <label for="">Set Reminder</label>
            <input v-model="reminder" type="checkbox" name="remminder" id=""/>
        </div>  
        <input type="submit" value="Save Task" class="btn btn-block">
    </form>
</template>

<script>
export default {
    name: "AddTask", 
    data(){
        return{
            text: '', 
            day: '', 
            reminder: false
        }
    }, 
    methods: {

        onSubmit(e){
            e.preventDefault();
            if(!this.text){
                alert("Text is missing");
                return
            }
            const newTask = {
                id: Math.floor(Math.random()*1000), 
                text: this.text, 
                day: this.day, 
                reminder: this.reminder
            }
            this.$emit('add-Task', newTask);
            console.log("newTask", newTask)
            this.text='';
            this.day='';
            this.reminder='';
        }, 
    }
}
</script>

<style scoped>
.add-form{
      margin-bottom: 4rem;
}
.form-control {
  margin: 2rem 0;
}
.form-control label {
  display: block;
}
.form-control input {
    width: 97%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>