<template>
    <ul class="todo-list">
      <li v-for="(todo, index) in todos" :key="todo.id" class="todo-item">
        <div
          class="checkbox-wrapper"
          :class="{ completed: todo.completed }"
          @click="toggleCompleted(todo)"
        >
          <span class="checkbox"></span>
        </div>
  
        <span :class="{ completed: todo.completed }" class="todo-text">
          {{ todo.text }}
        </span>
  
        <button @click="deleteTodo(index)" class="delete-button">X</button>
      </li>
    </ul>
  </template>
  
  <script>
  export default {
    name: "TodoItemList",
    props: {
      todos: {
        type: Array,
        required: true,
      },
    },
    methods: {
      toggleCompleted(todo) {
        this.$emit("toggle-completed", todo); // Emit the toggle event to the parent
      },
      deleteTodo(index) {
        this.$emit("delete-todo", index); // Emit the delete event to the parent
      },
    },
  };
  </script>
  
  <style lang="scss" scoped>
  
  .todo-list {
  list-style: none;
  padding: 0;
  
  .todo-item {
    display: flex;
    align-items: center;
    padding: 15px 0;
    border-bottom: 1px solid #eee;
    
    .checkbox-wrapper {
      width: 24px;
      height: 24px;
      border: 2px solid #ddd;
      border-radius: 50%;
      margin-right: 15px;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      
      &.completed {
        background-color: #ff5757;
        border-color: #ff5757;
      }
    }

    .todo-text {
      flex: 1;
      font-size: 16px;
      color: #333;
      
      &.completed {
        text-decoration: line-through;
        color: #999;
      }
    }

    .delete-button {
      padding: 5px 10px;
      background: none;
      border: none;
      color: #999;
      cursor: pointer;
      font-size: 18px;
      
      &:hover {
        color: #ff5757;
      }
    }
  }
}
</style>