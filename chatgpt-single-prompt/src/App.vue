<template>
  <div class="container mx-auto p-10">
    <h1 class="text-3xl font-bold mb-4">Todos</h1>
    <div class="flex">
      <todo-list class="w-3/4" @edit="startEdit"></todo-list>
      <div class="ml-10">
        <button class="bg-green-500 text-white rounded p-2" @click="showAddForm = true">
          Add Todo
        </button>
        <todo-form :isOpen="showAddForm" @close="showAddForm = false"></todo-form>
      </div>
    </div>
    <edit-todo-form :isOpen="currentEditTodo !== null" :todo="currentEditTodo" @close="currentEditTodo = null"></edit-todo-form>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import TodoForm from './components/TodoForm.vue'
import EditTodoForm from './components/EditTodoForm.vue'

export default {
  components: {
    TodoList,
    TodoForm,
    EditTodoForm
  },
  data() {
    return {
      showAddForm: false,
      currentEditTodo: null
    }
  },
  methods: {
    startEdit(todo) {
      this.currentEditTodo = todo
    }
  }
}
</script>
