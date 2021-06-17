<template>
<div class="container">
<Header title="TASK TRACKER" />
<AddTask @add-task="AddTask" />
<Tasks @toggle-reminder="toggleReminder"  
@delete-task="deleteTask"  :tasks= "tasks" />
</div>
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask'

export default {
  name: 'App',
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
methods: {
  addTask(task){
    this.tasks = [...this.tasks, task]
  },
  deleteTask(id) {
    if(confirm('Are you sure want to delete?')){
    this.tasks = this.tasks.filter((task)=> task.id !==id)
  }
  },
  toggleReminder(id){
    this.tasks = this.tasks.map((task)=> 
    task.id === id ? {...task,reminder: !task. reminder}: task
    )
  },
} ,
created(){
  this.tasks = [{
    id:1,
    text: 'Interview',
    day: 'june 24 at 02:30PM',
    reminder: true,
  },
  {
    id:2,
    text: 'Joining',
    day: 'june 27 at 10:30AM',
    reminder: true,

  },
  {
    id:3,
    text: 'Meeting',
    day: 'june 28 at 05:30AM',
    reminder: false,
  },

  ]
}
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=popins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'poppins', sans-serif;
}
.container {
  max-width:500px;
  margin: 30px auto;
  overflow:auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding:30px;
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
  font-size:15px;
  font-family: inherit;

}

</style>
