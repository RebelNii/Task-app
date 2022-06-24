<template>
    <!--@dblclick means double click-->
    <div @dblclick="$emit('toggle-reminder',task.id)" v-bind:class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>{{task.text}}
        <i v-on:click="onDelete(task.id)" class="fas fa-times"></i>
        </h3>
        <p>{{task.day}}</p>
    </div>
</template>

<script>
    export default{
        name: 'Task-app',
        props: {
            task: Object
        },
        methods: {
            onDelete(id) {
                this.$emit('delete-task', id)
            }
        },
        emits: ['toggle-reminder']
    }
</script>

<style scoped>
    div{
        margin: 5px;
        cursor: pointer;
        padding: 10px 20px;
    }

    .task.reminder{
        border-left: 5px solid green
    }

    .fas{
        color: red;
    }

    h3{
        font-family: Verdana, Geneva, Tahoma, sans-serif;
        font-size: 20px;
        font-weight: 300;
        margin-bottom: 5px;
    }

    p{
        font-family: Georgia, 'Times New Roman', Times, serif;
        font-size: 14px;
        margin-bottom: 10px;
    }

</style>