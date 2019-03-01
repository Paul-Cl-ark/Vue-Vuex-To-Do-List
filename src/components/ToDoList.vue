<template>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      {{ todo.text }}
      <span @click="deleteTodo(todo.id)">x</span>
    </li>
  </ul>
</template>

<script>
import { store } from '../store.js'
export default {
  name: 'ToDoList',
  data () {
    return {todos: store.state.todos}
  },
  methods: {
    deleteTodo (id) {
      this.$emit('deleteTodo', id)
    }
  }
  // computed: {
  //   remaining () {
  //     return this.todos.filter(todo => !todo.completed).length
  //   }
  // }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  max-width: 200px;
  margin: auto;
  margin-top: 10px;
}
li {
  margin: 5px;
}
</style>
