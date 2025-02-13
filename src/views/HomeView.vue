<template>
  <div>
    <h1>Home</h1>
    <TodoList />
  </div>
</template>

<script>
import TodoList from "@/components/TodoList.vue"; // Use the original TodoList component

export default {
  name: "HomeView",
  components: {
    TodoList,
  },
};
</script>