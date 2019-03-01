<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld/>
    <Input @addTodo="addTodo"/>
    <ToDoList :todos="todos" @deleteTodo="deleteTodo"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import Input from './components/Input'
import ToDoList from './components/ToDoList'
import { store } from './store.js'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Input,
    ToDoList
  },
  data () {
    return {
      last_id: 0,
      todos: []
    }
  },
  methods: {
    addTodo (todo) {
      let newTodo = {
        id: ++this.last_id,
        text: todo,
        components: false,
        editing: false
      }
      store.state.todos.push(newTodo)
    },
    deleteTodo (id) {
      return this.$delete(store.state.todos, id - 1)
    }
  }
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
