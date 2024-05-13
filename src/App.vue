<template>
    <div class="container"> 
    <div class="row"> 
      <div class="card p-5 mt-5"> 
      <h1>Todo List App</h1> 
      
        <form action="#"> 
          <div class="form-group"> 
            <label for="task">Task</label> 
            <input type="text" name="task" id="task" placeholder="I will do something..." class="form-control my-3" v-model="title"> 
          </div> 
          <div class="form-check my-3"> 
            <input type="checkbox" name="urgent" id="urgent" class="form-check-input" v-model="priority"> 
            <label class="form-check-lable" for="urgent" >
              important</label> 
          </div> 
          <div>
            <button type="button" class="btn btn-primary" @click="saveTask()">Save Task</button>
          </div>
        </form> 
    </div> 
    </div> 
    <h1>List all the Tasks</h1>
    <div class="row">
      <p class="text-center" v-if="tasks.length === 0">
          Ohh wow! you have done all tasks
        </p>
        <p class="text-center" v-else>Here are all the tasks</p>
      <div class="alert alert-secondary" role="alert" v-for="task in tasks" :key="task.title">
        {{task.title}}
      A simple secondary alert—check it out!
      </div>
      <div class="alert alert-success" role="alert" v-for="task in filteredTasks" :key="task.title">
        {{task.title}}
      A simple success alert—check it out!
  
    </div>
  </div>
  </div>
      
      
 
</template>

<script>
export default {
  name:"app",
  data() {
    return {
        title:"",
        priority:"",
        tasks:[
          {title:"this our first task", priority:false},
          {title:"this our second task", priority:false},
          {title:"this our third task", priority:false},
          {title:"this our fouth task", priority:false},
        ],
      }
    
  },
  methods:{
    saveTask(){
      this.tasks.push({title:this.title, priority:this.priority});
            
      
    }
  },
 computed:{
   filteredTasks(){
     return this.tasks.filter(task => task.priority === true)
   }
 }
 
   
}
</script>

<style>


</style>
