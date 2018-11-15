<template>
    <div class="ToDoItem">
        <tr>
            <td>{{ todo.text }} </td>
            <td> {{ todo.completed }} </td>
            <td>
                <b-button outline-danger @click="deleteItem(todo)">x</b-button>
            </td>
        </tr>
    </div>
</template>

<script>

export default {
  name: 'to-do-item',
  props: ['todo'],
  methods: {
      deleteItem(todo) {
          this.$emit('delete', todo)
      }
  }
}
</script>

<style>
.ToDoItem {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>