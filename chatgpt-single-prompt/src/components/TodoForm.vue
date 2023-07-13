<template>
    <AppModal :isOpen="isOpen" @close="closeForm">
      <h2 class="text-xl font-bold mb-4">Add Todo</h2>
      <input v-model="title" type="text" placeholder="Title" class="border rounded p-2 w-full mb-3" />
      <textarea v-model="description" placeholder="Description" class="border rounded p-2 w-full mb-4" />
      <button class="bg-blue-500 text-white rounded p-2" @click="submitForm">
        Submit
      </button>
    </AppModal>
  </template>
  
<script>
import AppModal from './AppModal.vue'

export default {
  components: {
    AppModal
  },
  props: ['isOpen'],
    data() {
      return {
        title: '',
        description: ''
      }
    },
    methods: {
      submitForm() {
        const todo = {
          id: Date.now(),
          title: this.title,
          description: this.description
        }
        this.$emit('submitForm', todo)
      }
    }
  }
  </script>