<template>
  <div>
    <h1>About</h1>
    <div class="cvb">
      <TodoInput @add-todo="addTodo" />
    <TodoItemList
      :todos="todos"
      @toggle-completed="toggleCompleted"
      @delete-todo="deleteTodo"
    />
    </div>
  </div>
</template>

<script>
import TodoInput from "@/components/TodoInput.vue";
import TodoItemList from "@/components/TodoItemList.vue";

export default {
  name: "AboutView",
  components: {
    TodoInput,
    TodoItemList,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.unshift({
        id: Date.now(),
        text: newTodo,
        completed: false,
      });
    },
    toggleCompleted(todo) {
      todo.completed = !todo.completed;
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>
<style>

.cvb{
  width: 30%;
  margin-inline: 35%;
 
}
</style>