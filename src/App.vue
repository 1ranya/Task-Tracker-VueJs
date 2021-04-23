<template>
  <div class="container">
    <Header title="Task Tracker"/>
    <AddTask $emit="addTask"/>
    <Tasks 
      @toggle-reminder="toggleReminder" 
      @delete-task="deleteTask" 
      :tasks="tasks"/>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import Header from './components/Header';
import Tasks from './components/Tasks';
import AddTask from './components/AddTask'

export default defineComponent({
  name: "App",
  components: {
    Header, 
    Tasks, 
    AddTask
  },
  data(){
    return{
      tasks: []
    }
  }, 
  methods:{
    deleteTask(id){
      if(confirm('Delete this Task! Are you sure?')){
        this.tasks = this.tasks.filter((task) =>
          task.id !== id )
      }
    },

    toggleReminder(id){
      console.log(id)
      this.tasks = this.tasks.map((task) => 
        task.id === id 
        ? {...task, reminder: !task.reminder}
        : task
      )
    }, 

    addTask(){
      
    }
  },
  created(){ //life cycle hook 
    this.tasks = [
      {
        id:1, 
        text:'Doctors Appointment',
        day:'Mai 1st at 3pm '
      },
      {
        id:2, 
        text:'Work meeting',
        day:'Mai 5st at 4pm '
      },
      {
        id:3, 
        text:'Dentist Appointment',
        day:'Mai 11st at 1pm '
      },
      {
        id:4, 
        text:'Call Friends',
        day:'Mai 21st at 3pm '
      }
    ]
  }
});
</script>

<style>
#app {
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.btn{
  color: white;
  background-color: #2c3e50;
  margin-right: 0.2rem;
  width: 10rem;
  height: 2rem;
  border-style: none
}
</style>
