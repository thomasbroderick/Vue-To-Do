<template>
  <div id="app">
    <div class="ToDo">
      <h1 class="ToDo-Header">To Do List</h1>
        <b-table striped bordered hover :items="list" :fields="fields">
          <template slot="delete" slot-scope="cell">
            <b-btn outline-danger size="sm" @click.stop="deleteToDo(todo)">x</b-btn>
          </template>
        </b-table>
      
    </div>
    <input type="text" v-model="todo" placeholder="Enter new item" v-on:keyup.enter="createNewToDo()"/>
    <button class="ToDo-Add" @click="createNewToDo()">+</button>
  </div>
</template>

<script>
import ToDoItem from './components/ToDoItem.vue'

export default {
  name: 'app',
  components: {
    ToDoItem
  },
  data() {
    return {
      fields: [
        'text', 'completed', 'delete'
      ],
      list: [
        {
          id: 1,
          text: 'Read Vue.js documentation',
          completed: false
        },
        {
          id: 2,
          text: 'Make a ToDo App',
          completed: false
        }
      ],
      todo: ''

    }
  },

  methods: {
    createNewToDo() {
      var newID = this.list.length + 1;
      this.list.push({ id: newID, text: this.todo, completed: false});
      this.todo = '';
    },

    deleteToDo(todo) {
      var position = todo.id - 1;
      this.list.splice(position, 1);
    }
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
.ToDo-Header {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  color: aquamarine

}
</style>
