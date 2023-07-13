<template>
  <div id="app" class="bg-gray-200 min-h-screen p-4 flex flex-col lg:flex-row lg:items-start lg:justify-center">
    <div class="lg:w-2/3 lg:mr-4">
      <TodoItem
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @edit-todo="showEdit"
        @delete-todo="deleteTodo"
      />
    </div>
    <div class="lg:w-1/3">
      <button @click="showAddTodo = true" class="w-full lg:w-auto bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mb-4">Add</button>
      <AddTodo :show="showAddTodo" @create-todo="addTodo" @close="showAddTodo = false" />
      <EditTodo v-if="currentTodo" :show="showEditTodo" :todo="currentTodo" @update-todo="editTodo" @close="showEditTodo = false" />
    </div>
  </div>
</template>

<script>
import TodoItem from './components/TodoItem.vue';
import AddTodo from './components/AddTodo.vue';
import EditTodo from './components/EditTodo.vue';

export default {
  name: 'App',
  components: {
    TodoItem,
    AddTodo,
    EditTodo
  },
  data() {
    return {
      todos: [],
      currentTodo: null,
      showAddTodo: false,
      showEditTodo: false
    }
  },
  methods: {
    addTodo(todo) {
      this.todos.push({ ...todo, id: Date.now() });
      this.showAddTodo = false;
    },
    editTodo(updatedTodo) {
      this.todos = this.todos.map(todo =>
        todo.id === updatedTodo.id ? updatedTodo : todo
      );
      this.showEditTodo = false;
      this.currentTodo = null;
    },
    deleteTodo(todoToDelete) {
      this.todos = this.todos.filter(todo => todo.id !== todoToDelete.id);
    },
    showEdit(todo) {
      this.currentTodo = todo;
      this.showEditTodo = true;
    }
  }
}

</script>