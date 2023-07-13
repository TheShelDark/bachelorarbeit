<template>
    <div class="mt-5">
      <div v-for="todo in todos" :key="todo.id" class="bg-white rounded p-4 mb-4 shadow-md">
        <h2 class="text-xl font-bold mb-2">{{ todo.title }}</h2>
        <p class="mb-4">{{ todo.description }}</p>
        <button class="bg-blue-500 text-white rounded p-2 mr-2" @click="startEdit(todo)">
          Edit
        </button>
        <button class="bg-red-500 text-white rounded p-2" @click="deleteTodo(todo.id)">
          Delete
        </button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        todos: [] // Fetch or manage todos as required
      }
    },
    methods: {
      startEdit(todo) {
        this.$emit('edit', todo)
      },
      deleteTodo(id) {
        // Implement delete functionality
      }
    }
  }
  </script>
  