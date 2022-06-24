<template>
    <header>
        <h1>{{title}}</h1>
        <Button v-show="homePage" @btnClick="$emit('toggle-addBtn')" v-bind:text="showAddTask ? 'Close' : 'Add Task'" :color="showAddTask ? 'red' : 'green'" />
    </header>
</template>


<script>

import Button from './Button';

export default {
    name: 'Header-app',
    props: {
        title: String,
        showAddTask: Boolean
    },
    components: {
        Button,
    },
    emits: ['toggle-addBtn'],
    computed: {
        homePage(){
            if(this.$route.path === '/home'){
                return true
            }else{
                return false
            }
        }
    },
}
</script>

<style scoped>
header {
    display: flex;
    align-items: flex-start;
    justify-content: flex-start;
    margin-bottom: 20px;
}

header h1{
    color: #333;
}
</style>