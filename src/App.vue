<template>
  <div class="container">
    <Header title="Task Tracker"/>
    <Tasks :tasks="tasks"/>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import Header from './components/Header';
import Tasks from './components/Tasks';

export default defineComponent({
  name: "App",
  components: {
    Header, 
    Tasks
  },
  data(){
    return{
      tasks: []
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
  font-family: Avenir, Helvetica, Arial, sans-serif;
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
