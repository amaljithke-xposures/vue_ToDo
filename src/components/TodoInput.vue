<template>
    <div>
      <!-- Heading with Icon -->
      <h1 class="todo-heading">
        <img src="@/assets/listing.png" alt="Todo App Icon" class="heading-icon" />
        To-Do List
      </h1>
  
      <!-- Input and Add button Section -->
      <div class="input-container">
        <input
          v-model="newTodo"
          type="text"
          class="todo-input"
          placeholder="Add your task"
        />
        <button @click="addTodo" class="add-button">ADD</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: "TodoInput",
    data() {
      return {
        newTodo: "",
      };
    },
    methods: {
      addTodo() {
        if (this.newTodo.trim() !== "") {
          this.$emit("add-todo", this.newTodo); // Emit the new todo to the parent
          this.newTodo = ""; // Clear the input
        }
      },
    },
  };
  </script>
  
  <style lang="scss" scoped>
.todo-container {
  width: 100%;
  max-width: 500px;
  padding: 20px;
  margin: 0 auto;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(31, 0, 0, 0.1);
}

.todo-heading {
  display: flex;
  align-items: center;
  font-size: 28px;
  color: #1a237e;
  margin-bottom: 30px;
  
  .heading-icon {
    width: 32px;
    height: 32px;
    margin-right: 10px;
  }
}

.input-container {
  position: relative;
  display: flex;
  align-items: center;
  margin-bottom: 30px;
  background: #e2d3d3;
  border-radius: 999px;
  padding: 5px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.05);

  .todo-input {
    flex: 1;
    padding: 15px 20px;
    font-size: 16px;
    border: none;
    background: transparent;
    outline: none;
    color: #333;
    
    &::placeholder {
      color: #9e9e9e;
    }
  }

  .add-button {
    min-width: 100px;
    padding: 12px 25px;
    background-color: #ff5757;
    color: white;
    border: none;
    border-radius: 999px;
    font-weight: 600;
    font-size: 16px;
    cursor: pointer;
    transition: background-color 0.2s ease;

    &:hover {
      background-color: #ff4242;
    }
  }
}

  </style>