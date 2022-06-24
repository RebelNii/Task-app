<template>
  <div class="con">
    <Header v-on:toggle-addBtn="toggleAdd" title='Task' v-bind:showAddTask="showAddTask" />
    
    <router-view :showAddTask="showAddTask"></router-view>
    <Footer />
  </div>
</template>

<script>

import Header from './components/Header';

import Footer  from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Header,
    
    Footer
},
  data() {
    return{
    
    showAddTask: false
    }
  },
  methods:{

    toggleAdd(){
      this.showAddTask = !this.showAddTask
    }

}
}
</script>

<style>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body{
  font-size: 16px;
  color: #000;
  font-weight: 500;
}



.con {
  text-align: center;
  margin: 30px auto;
  padding: 30px;
  max-width: 500px;
  min-height: 300px;
  border: 1px solid aqua;
  overflow: auto;
  border-radius: 5px;
}

.btn{
  display: inline-block;
  background: #000;
  border: none;
  padding: 10px 20px;
  margin-top: 5px;
  margin-bottom: 5px;
  margin-left: 260px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus{
  outline: none;
}
</style>
