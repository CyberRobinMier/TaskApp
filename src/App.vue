<template>
<div class="container">
   <Header title="Task Tracker" />
   <AddTask @add-task="addTask"/>
   <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" /> <!--here we finally make it into a proper method -->

</div>
 <!-- Tasks deals with an array and is dynamic, 
 which is why it needs binding  to the tasks down in data-->
  
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask.vue'



export default {
  name: 'App',
  components: {
    Header,
    Tasks, 
    AddTask,
  },
  data(){
    return {
      tasks:[]
    }
    },
    methods:{
      addTask(task){
        console.log("adding a task...")
        this.tasks=[...this.tasks, task]
        
      },
      deleteTask(id){ //changing the array of tasks
        if(confirm('Are you sure?')){  //creates a popup asking if u sure. automatically parses 'ok' and 'cancel' to true/false
          this.tasks =this.tasks.filter((task)=>task.id !==id)
        };
      },
      toggleReminder(id){ //updating one task (object) in array of tasks
        this.tasks = this.tasks.map((task)=> task.id===id? {...task, reminder: !task.reminder}:task) //map, if task id is same, then spread task, only change reminder. if not return task
      },
   
    },
    created() {
      this.tasks = [
        {
          id:1,
          text: 'Work on Vue',
          day: 'February 15th at 8:00am',
          reminder: true
        },
         {
          id:2,
          text: 'Check in with boiler people',
          day: 'February 15th at 11:00am',
          reminder: false
        },
         {
          id:3,
          text: 'Commit to Github',
          day: 'February 15th at 10:00am',
          reminder: false
        },
      ]
    }
  }
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
}
.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
