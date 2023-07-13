<template>
  <div class="max-w-lg mx-auto pt-12">
    <h1 class="text-2xl font-bold mb-4 text">Todo-Liste:</h1>
    <template :key="todo.id" v-for="todo in todos">
      <TodoItem :todo="todo" @edit="edit(todo)" @remove="remove(todo)"/>
    </template>
    <AddTodo @submit="addTodo" class="my6"/>
    <EditTodo :todo="selectedTodo" v-if="selectedTodo" @submit="updateTodo" @close="closeEdit"/>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem.vue';
import AddTodo from '@/components/AddTodo.vue';
import EditTodo from '@/components/EditTodo.vue';

export default {
  components: {
    TodoItem,
    AddTodo,
    EditTodo
  },
  data() {
    return {
      todos: [{ id: 1, title: 'Todo 1' }, { id: 2, title: 'Todo 2' }],
      selectedTodo: null
    };
  },
  methods: {
    edit(todo) {
      this.selectedTodo = todo;
    },
    remove(todo) {
      const index = this.todos.indexOf(todo) 
      this.todos.splice(index, 1);
    },
    addTodo(newTodo) {
      this.todos.push(newTodo);
    },
    updateTodo(updatedTodo) {
      const index = this.todos.findIndex(todo => todo.id === updatedTodo.id);
      this.todos.splice(index, 1, updatedTodo);
    },
    closeEditPopup() {
      this.selectedTodo = null;
    }
  }
}
</script>