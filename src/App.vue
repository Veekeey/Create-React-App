<template>
 <div class="tracker">
  <TrackerHeader @show-todo-form="toggleForm" 
  title="To do list" 
  :changeButton="showForm"/>
  <div v-show="showForm">
    <AddTodo @add-task="addTask"/> 
  </div>
  
  <Tasks @toggle-reminder="toggleReminder" 
  @delete-task="deleteTask" 
  :tasks="tasks"/> 
 </div>
</template>

<script>
import TrackerHeader from './components/TrackerHeader.vue'
import Tasks from './components/Tasks.vue'
import AddTodo from './components/AddTodo'


export default {
  name: 'App',
  components: {
    TrackerHeader,
    Tasks,
    AddTodo
  },
  data(){
    return {
      tasks: [],
      showForm: false
    }
  },
  methods: {
    toggleForm(){
      this.showForm = !this.showForm
    },
    addTask(task){
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id){
      if(confirm('Are you sure?')){
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task)=> task.id === id ? {...task, reminder: !task.reminder} : task)
    }
    
  },
  created(){
    this.tasks = [
      {
        id: 1,
        description: 'wash my clothes',
        time: '10.00am',
        reminder: true
      },
      {
        id: 2,
        description: 'Clean the kitchen',
        time: '11.00am',
        reminder: true
      },
      {
        id: 3,
        description: 'Read a book',
        time: '2.00pm',
        reminder: false
      }
    ]
  },
  
}
</script>

<style>
  .tracker {
    width: 40%;
    border: 1px solid #eeee;
    background-color: #f4f4f4;
    margin: 0 auto;
    margin-top: 3rem;
  }

  .btn {
    display: inline-block;
    background-color: black;
    color: #fff;
    border: none;
    padding: 10px 10px;
    border-radius: 5px;
    height: 35px;
    margin-top: 25px;
}

</style>
