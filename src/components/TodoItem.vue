<template>
  <div class='todo-item' v-bind:class='{"is-complete":x.completed}'> 
    <p>
      <input type="checkbox" v-on:change="markComplete">  
      {{x.title}}
      <button @click='$emit("del-todo", x.id)' class='del'>x</button> 
    </p>
  </div>
</template>

<script>
export default {
  name: 'TodoItem',
  props: ['x'],
  methods: {
    markComplete(){
      this.x.completed = !this.x.completed
    }
  }
}
</script>

<style scoped>
  .todo-item {
    background: whitesmoke;
    padding: 10px;
    border-bottom: 1px lightgray dotted;
  }
  .is-complete {
    text-decoration: line-through;
  }
  .del {
      background: red;
      color: white;
      border: none;
      padding: 5px 9px;
      border-radius: 50%;
      cursor: pointer;
      float: right;
  }
  
</style>