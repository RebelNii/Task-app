<template>
    <h1>Home</h1>
    <div v-show="showAddTask" >
      <Add v-on:new-task="addTask" />
    </div>
    <Tasks @toggle-reminder="ToggleReminder" @delete-two="deleteTask" v-bind:tasks="tasks" />
</template>

<script>
import Tasks from '../components/Tasks';
import Add  from '../components/Add.vue';
export default {
    name: 'home-view',
    data(){
        return{
            tasks: [],
        }
    },
    props: {
        showAddTask: Boolean
    },
    components: {
        Tasks,
        Add,
    },
     methods:{

    async addTask(task){
      const res = await fetch('api/tasks', {
        method: 'POST',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(task)
      })
      const data = await res.json()


        this.tasks = [...this.tasks, data]
    },


    //function to delete task
    async deleteTask(id){
      //we will use the id as an identifier to delete tasks
      if(confirm('Are you Sure?')){

        const res = await fetch(`api/tasks/${id}`, {
          method: 'DELETE',

        })
        res.status === 200 ? (this.tasks = this.tasks.filter((task) => 
          task.id !== id)) : alert('Cannot Delete')

      }
    },


    async ToggleReminder(id){
      
      //assigning a new variable to get a specific task so toggling reminder can be easily achieved
      const taskToggle = await this.getTask(id)

      const updateTask = {...taskToggle, reminder: !taskToggle.reminder}

      const res = await fetch(`api/tasks/${id}`, {
        method: 'PUT', //put is for updates
        headers: {
          'Content-type': 'application/json'
        },//headers since we'll be sending data
        body: JSON.stringify(updateTask)
        
      })

      console.log(updateTask)
      const data = await res.json()



        //So we just want to just the reminder value, map() returns us new value
        this.tasks = this.tasks.map((task) => task.id === id
        ? {...task, reminder: data.reminder} : task) 
    },


    //function to fetch all tasks
    async getTasks() {
        const res = await fetch('api/tasks');
        const data = await res.json()
        return data
    },

    //function to fetch a specific task so updating data will be easily achieved
    async getTask(id) {
        const res = await fetch(`api/tasks/${id}`);
        const data = await res.json()
        console.log(data)
        return data
    },


  },
  async created() {
    this.tasks = await this.getTasks()
  }
}
</script>