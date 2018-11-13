<template>
    <div class="ToDoItem">
        <tr>
            <td>{{ todo.text }} </td>
            <td> Edit </td>
            <td> Delete </td>
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