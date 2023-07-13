<template>
    <div>
      <h1>Todo-Liste:</h1>
      <div v-for="todo in todos" :key="todo.id">
        <span>{{ todo.title }}</span>
        <button @click="edit(todo)">Edit</button>
        <button @click="deleteTodo(todo)">Delete</button>
      </div>
      <button @click="showAddPopup = true">Add</button>
      <div class="popup" v-if="showAddPopup">
        <h1>Add a new todo</h1>
        <input type="text" v-model="title">
        <textarea v-model="description"></textarea>
        <button @click="add">Save</button>
        <button @click="showAddPopup = false">Cancel</button>
      </div>
      <div class="popup" v-if="currentTodo">
        <h1>Edit {{ currentTodo.title }}</h1>
        <input type="text" v-model="currentTodo.title">
        <textarea v-model="currentTodo.description"></textarea>
        <button @click="update">Save</button>
        <button @click="currentTodo = null">Cancel</button>
      </div>
    </div>
  </template>
  
  <style>
  .popup {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    background: rgba(0, 0, 0, 0.7);
    z-index: 999;
  }
  
  .popup h1,
  .popup input,
  .popup textarea {
    display: block;
    margin-bottom: 10px;
  }
  
  .popup input,
  .popup textarea {
    width: 100%;
    padding: 5px;
    border: none;
    border-radius: 3px;
    font-size: 16px;
  }
  
  .popup button {
    padding: 10px;
    border: none;
    border-radius: 3px;
    color: #fff;
    background: #333;
    cursor: pointer;
  }
  
  .popup button + button {
    margin-left: 10px;
  }
  </style>
  
  <script>
  export default {
    data() {
        return {
            todos: [{ id: 1, title: 'Todo 1' }, { id: 2, title: 'Todo 2' }],
            currentTodo: null,
            showAddPopup: false,
            title: '',
            description: ''
            };
    },
    methods: {
        edit(todo) {
            this.currentTodo = todo;
        },
        deleteTodo(todo) {
            const index = this.todos.indexOf(todo);
            this.todos.splice(index, 1);
        },
        add() {
            const newTodo = {id: this.todos.length + 1, title: this.title, description: this.description};
            this.todos.push(newTodo);
            this.showAddPopup = false;
        },
        update() {
            this.currentTodo = null;
        }
    }
  };
  </script>