<template>
    <form v-on:submit="onSubmit" action="">
        <div class="form">
        <div class="addTask">
            <label for="">Task</label><br>
            <input class="input" v-model="task" type="text" name="task" placeholder="Add Task">
        </div>
        <div class="addDate">
            <label for="">Date</label><br>
            <input class="input" v-model="date" type="text" name="date" placeholder="Add Date">
        </div>
        <div class="addReminder">
            <label for="">Reminder</label>
            <input class="input" v-model="reminder" type="checkbox" name="reminder" placeholder="Add Reminder">
        </div>
        
        <input class="btn-submit" type="submit" name="save" value="submit">
        
        </div>
    </form>
</template>

<script>
    export default {
        name: 'AddTask',
        data(){
            return {
                task: '',
                date: '',
                reminder: false
            }
        },
        methods: {
            onSubmit(e){
                e.preventDefault();
                if(!this.task){
                    alert('Please add a task')
                    return
                }
                const newTask = {
                    //id: Math.floor(Math.random() * 100000),
                    text: this.task,
                    day: this.date,
                    reminder: this.reminder
                }

                console.log(newTask)
                this.$emit('new-task', newTask)

                this.task ='',
                this.day ='',
                this.reminder =''
            }
        }
    }
</script>

<style scoped>
    form{
        display: flex;
        justify-content: center;
        align-content: center;
        flex-direction: row;
        padding: 10px;
        margin: 10px;
    }

    .form{
        position: relative;
        width: 100%;
    }
    .form > div{
        margin: 3px;
    }

    .input{
        width: 100%;

    }

    .form .addReminder{
        display: flex;
        justify-content: space-between;
        margin: 7px 0;
        
    }
  

    .btn-submit{
        color: #fff;
        background-color: #333;
        border: none;
        cursor: pointer;
        width: 100%;
        padding: 10px;
        margin: 10px 0;
        border-radius: 1px 1px;
        text-align: center;
        text-transform: uppercase;
    }
</style>