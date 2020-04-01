<template>
  <div id="app">
    <!-- TODO add asset logo below -->
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <Header/>
    <AddTask v-on:add-task='addTask'/>
    <Todos v-bind:todos="todos" v-on:del-todo='deleteTodo' />
  </div>
</template>

<script>
  import Todos from './components/Todos';
  import AddTask from './components/AddTask';
  import Header from './components/Layouts/Header';

export default {
  name: 'App',
  components: {
    Todos,
    Header,
    AddTask
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: 'Task One',
          completed: false
        },
        {
          id: 2,
          title: 'Task Two',
          completed: false
        },
        {
          id: 3,
          title: 'Task Three',
          completed: false
        }
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(x => x.id !== id);
    },
    addTask(newTask){
      this.todos = [...this.todos, newTask];
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  line-height: 1.4;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: white;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover {
  background: #666;
}
#app {
}
</style>
