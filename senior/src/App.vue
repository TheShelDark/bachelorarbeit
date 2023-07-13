<template>
  <!-- Main Canvas -->
  <div class="min-h-screen min-w-screen flex flex-col md:justify-center items-center mt-8 md:mt-0">
    <Header text="Todo App by Sebastian Gerz" icon="true" />
    
    <div class="md:grid md:grid-cols-2 items-start gap-4 flex flex-col-reverse mt-6 border-2 rounded-lg p-6">
        <ul>
          <TodoItem v-for="todo in todos" @edit="onEdit(todo)" @delete="onDelete(todo)" :todo="todo" />
        </ul>
        <Button text="Add Todo" @click="onAdd" @keyup.esc="onClose"/>
    </div>

    <Modal v-if="todoObj" @close="onClose" title='Save Todo'>
      <TodoForm :todo="todoObj" @save="onSave"/>
    </Modal>

  </div>
</template>

<script setup>

  import { ref, computed } from "vue"
  import Header from "./components/Header.vue";
  import Button from "./components/Button.vue"
  import Modal from "./components/Modal.vue";
  import TodoForm from "./components/TodoForm.vue";
  import TodoItem from "./components/TodoItem.vue";
  import Searchbar from "./components/Searchbar.vue";

  /* Todo Operations */
  const todos = ref([
    {
      id: 1,
      title: "Doctors Appointment",
      description: "Go to the doctor at 2pm",
      checked: true,
    },
    {
      id: 2,
      title: "Meeting at School",
      description: "Meeting of parents in school",
      checked: true,
    },
    {
      id: 3,
      title: "Food Shopping",
      description: "buy Oranges, Bananas and Cucumbers",
      checked: false,
    },
  ])

  const todoObj = ref()
  const searchQuery = ref('')

  function onSave(newTodo) {
    todoObj.value = null

    if (!newTodo.id) {
      newTodo.id = Math.random()
      todos.value.push(newTodo)
      return
    }

    let todoToBeUpdated = todos.value.find((todo) => todo.id === newTodo.id)
    Object.assign(todoToBeUpdated, newTodo)
  }

  function onDelete(todoToBeRemoved) {
    todos.value = todos.value.filter((todo) => todo.id !== todoToBeRemoved.id)
  }

  function onAdd() {
    todoObj.value = { };
  }

  function onEdit(todo) {
    todoObj.value = todo
  }

  function onClose() {
    todoObj.value = null
  }

  /* Filtered Todos */
  const filtered_todos = computed(() => 
    todos.value.filter((todo) => todo.title.toLowerCase().indexOf(searchQuery.value.toLowerCase()) != -1)
  )

</script>

