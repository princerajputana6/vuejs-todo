<template>
  <div id="app">
    <AddTodo />
    <Todos />
  </div>
</template>

<script>
import AddTodo from './components/AddTodo.vue';
import Todos from './components/Todos.vue';

export default {
  name: 'App',
  components: {
    AddTodo,
    Todos,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

  margin: auto;
  margin-top: 60px;
  width: 500px;
  height: 600px;
  box-shadow: 20px 20px 50px 15px grey;
  overflow-y: auto;
}
</style>
