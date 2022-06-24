<template>
    <div v-for="task in tasks" :key="task.id">
        <Task @toggle-reminder="$emit('toggle-reminder',task.id)" 
        v-on:delete-task="$emit('delete-two', task.id)" v-bind:task="task" />
    </div>
</template>

<script>
    import Task from './Task.vue'

    export default {
        name: 'Tasks-app',
        props: {
            tasks: Array
        },
        components: {
            Task,
        },
        emits: ['delete-two','toggle-reminder']
    }
</script>

<style>


    
</style>