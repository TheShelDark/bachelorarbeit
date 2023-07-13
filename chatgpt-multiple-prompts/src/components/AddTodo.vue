<template>
    <div v-if="show" class="fixed z-10 inset-0 overflow-y-auto" aria-labelledby="modal-title" role="dialog" aria-modal="true">
      <div class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0">
        <div class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity" aria-hidden="true"></div>
        <span class="hidden sm:inline-block sm:align-middle sm:h-screen" aria-hidden="true">&#8203;</span>
        <div class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full">
            <div class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
                <h1 class="text-lg">Add Todo</h1>
                <input type="text" v-model="title" placeholder="Todo title" class="mt-2 w-full px-2 py-1 border border-gray-300 rounded">
                <textarea v-model="description" placeholder="Todo description" class="mt-2 w-full px-2 py-1 border border-gray-300 rounded"></textarea>
                <button @click="createTodo" class="mt-3 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Create</button>
            </div>
        </div>
      </div>
    </div>
</template>
  
  <script>
  export default {
    props: ['show'],
    data() {
      return {
        title: '',
        description: ''
      }
    },
    methods: {
      createTodo() {
        this.$emit('create-todo', { title: this.title, description: this.description });
        this.title = '';
        this.description = '';
      }
    }
  }
  </script>
  