<template>
  <div id="app">
    <todo_list/>
    
  </div>
</template>

<script>
import todo_list from './components/todo_list.vue'


export default {
  name: 'App',
  components: {
    todo_list
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
