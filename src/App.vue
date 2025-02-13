<template>
  <div id="app">
    <TodoList />
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';

export default {
  name: 'App',
  components: {
    TodoList
  }
};
</script>

<style>
#app {
  height: 100vh; /* Take full height of the viewport */
  display: flex; /* Enable Flexbox */
  justify-content: center; /* Center content horizontally */
  align-items: center; /* Center content vertically */
}
</style>
