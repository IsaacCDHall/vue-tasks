<template>
  <div>
    <div v-for="(x) in todos"
    :key="x.id">
      <TodoItem v-bind:x="x" v-on:del-todo='$emit("del-todo", x.id)'/>
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem.vue";
export default {
  name: 'Todos',
  components: {
    TodoItem
  },
  props: ['todos']
}
</script>

<style scoped>

</style>