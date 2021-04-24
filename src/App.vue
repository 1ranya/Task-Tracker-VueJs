<template>
  <div class="container">
    <Header :showAddTaskVar="showAddTaskVar" @show-add-task="showAddTask" title="Task Tracker"/>
    <div v-show="showAddTaskVar">
      <AddTask @add-task="addTask"/>
    </div>
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
      tasks: [], 
      showAddTaskVar: false 
    }
  }, 
  methods:{
    async deleteTask(id){
      if(confirm('Delete this Task! Are you sure?')){

        const res = await fetch(`api/tasks/${id}`, {
          method:'DELETE'
        })
        
        res.status === 200 
        ?(this.tasks = this.tasks.filter((task) =>
          task.id !== id))
        : alert(`Task can't be deleted`) 
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

    async addTask(task){
      const res = await fetch(`api/tasks`, {
        method: 'POST', 
        headers: {
          'content-type': 'application/json',
        },
        body: JSON.stringify(task)
      })
      const data = await res.json();
      this.tasks = [...this.tasks, data];
    },

    showAddTask(){
      this.showAddTaskVar = !this.showAddTaskVar
    }, 

    async fetchTasks(){
      const res = await fetch('api/tasks')
      const tasks = await res.json()
      return tasks
    }, 

    async fetchTask(id){
      const res = await fetch(`api/tasks/${id}`)
      const task = await res.json()
      return task
    }
  },
  async created(){ //life cycle hook 
    this.tasks = await this.fetchTasks()
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
.container{
  width: 50%;
  height: 50%;
  padding-left: 25%
}
</style>
