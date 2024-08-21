<template>
    <div class="todo-list">
      <h1>Todo List</h1>
      <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new todo" />
      <ul>
        <li v-for="(todo, index) in todos" :key="index">
          <input type="checkbox" v-model="todo.completed" />
          {{ todo.text }}
          <button @click="removeTodo(index)">Remove</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTodo: '',
        todos: []
      };
    },
    methods: {
      addTodo() {
        if (this.newTodo.trim() !== '') {
          this.todos.push({ text: this.newTodo, completed: false });
          this.newTodo = '';
        }
      },
      removeTodo(index) {
        this.todos.splice(index, 1);
      }
    }
  };
  </script>
  
  <style scoped>
  .todo-list {
    max-width: 400px;
    margin: auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  input[type="checkbox"] {
    margin-right: 10px;
  }
  
  button {
    margin-left: 10px;
    color: red;
    border: none;
    background: none;
    cursor: pointer;
  }
  </style>
  