<template>
  <div id="app">
    <div class="ToDo">
      <h1 class="ToDo-Header">Braxton Interview To Do List</h1>
        <b-table striped bordered hover :items="notCompleted" :fields="fields">
          <template slot="actions" slot-scope="row">
            
            <b-btn class="m-2" v-b-modal.modal1 size="sm" @click.stop="selected=row.item">Edit</b-btn>            
            <b-btn outline-danger size="sm" @click.stop="deleteToDo(row.item)">Delete</b-btn>
            
          </template>
        </b-table> 
    </div>
    <div>
      <b-modal id="modal1" title="Edit Item">
        <input v-model="selected.text">
        <div>
        <input type="checkbox" id="checkbox" class="m-2" v-model="selected.completed">
          <label for="checkbox">Completed</label>
        </div>
      </b-modal>
    </div>
    <input type="text" v-model="todo" placeholder="Enter new item" v-on:keyup.enter="createNewToDo()"/>
    <button class="ToDo-Add" @click="createNewToDo()">+</button>
  </div>
  
</template>

<script>

export default {
  name: 'app',
  components: {
    
  },
  data() {
    return {
      fields: [
        'text', 'completed', 'actions'
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
        },
        {
          id: 3,
          text: 'Crush Interview',
          completed: false
        }
      ],
      todo: '',
      selected: ''
    }
  },

  computed: {
    notCompleted: function () {
    return this.list.filter(function (todo) {
      return todo.completed === false
    })
  }
  },

  methods: {
    createNewToDo() {
      var newID = this.list.length + 1;
      this.list.push({ id: newID, text: this.todo, completed: false});
      this.todo = '';
    },

    deleteToDo(todo) {
      const position = this.list.indexOf(todo);
      this.list.splice(position, 1);
    },

    displayToDo(todo) {
    this.selected = todo;
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
}
.ToDo-Header {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  color: goldenrod;
  background-color: black;
  padding-top: 50px;
}

.b-btn {
  margin: 13px;
}
</style>
