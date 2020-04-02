<template>
  <div id="app">
    <h1> My Planner </h1>
    <hr>

    <router-view />
  </div>
</template>

<script>
import Todolist from '@/components/Todolist'
import Addtodo from '@/components/Addtodo'
export default {
  name: 'App',
  data() {
    return {
      todos: []
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
            .then(response => response.json())
            .then(json => {
              this.todos = json
            })
  },
  methods: {
    removeTodo (id) {
      this.todos = this.todos.filter(t=> t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  },
  components: {
Todolist, Addtodo
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
