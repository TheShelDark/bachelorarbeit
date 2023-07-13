<template>
  <div>
    <ToDoList :todos="todos" @open-add-todo="showAddToDo" @open-edit-todo="showEditToDo" @delete-todo="deleteToDo" />
    <AddToDo v-if="showAddToDoModal" @add-todo="addToDo" @close-add-todo="hideAddToDo" />
    <EditToDo v-if="showEditToDoModal" :todo="editingToDo" @edit-todo="editToDo" @close-edit-todo="hideEditToDo" />
  </div>
</template>

<script>
import ToDoList from "./components/TodoList.vue";
import AddToDo from "./components/AddTodo.vue";
import EditToDo from "./components/EditTodo.vue";
export default {
  components: {
    ToDoList,
    AddToDo,
    EditToDo
  },
  data() {
    return {
      todos: [
        { id: 1, title: "ToDo 1", description: "Description for ToDo 1" },
        { id: 2, title: "ToDo 2", description: "Description for ToDo 2" },
        { id: 3, title: "ToDo 3", description: "Description for ToDo 3" }
      ],
      showAddToDoModal: false,
      showEditToDoModal: false,
      editingToDo: {}
    };
  },
  methods: {
    showAddToDo() {
      this.showAddToDoModal = true;
    },
    hideAddToDo() {
      this.showAddToDoModal = false;
    },
    addToDo(todo) {
      const id = this.todos.length + 1;
      this.todos.push({ id, ...todo });
      this.hideAddToDo();
    },
    showEditToDo(todo) {
      this.editingToDo = todo;
      this.showEditToDoModal = true;
    },
    hideEditToDo() {
      this.showEditToDoModal = false;
    },
    editToDo(updatedToDo) {
      const index = this.todos.findIndex(todo => todo.id === updatedToDo.id);
      this.todos.splice(index, 1, updatedToDo);
      this.hideEditToDo();
    },
    deleteToDo(id) {
      const index = this.todos.findIndex(todo => todo.id === id);
      this.todos.splice(index, 1);
    }
  }
};
</script>