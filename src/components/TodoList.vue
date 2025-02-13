<template>
  <div class="todo-container">
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

    <!-- Todo List -->
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
  </div>
</template>

<script>
export default {
  name: "TodoApp",
  data() {
    return {
      newTodo: "",
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== "") {
        this.todos.unshift({
          id: Date.now(),
          text: this.newTodo,
          completed: false,
        });
        this.newTodo = ""; 
      }
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