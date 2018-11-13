<template>
  <div id="app">
    <div class="ToDo">
      <h1 class="ToDo-Header">To Do List</h1>
        <table class="ToDo-Table">
          <ToDoItem v-for="todo in list"
                    :todo="todo"
                    @delete="onDeleteItem"
                    :key="todo.id" />
        </table>
      
    </div>
  </div>
</template>

<script>
import ToDoItem from './components/ToDoItem.vue'

export default {
  name: 'app',
  components: {
    ToDoItem
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
