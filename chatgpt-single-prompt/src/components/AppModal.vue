<template>
    <div class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center" v-if="isOpen">
      <div class="bg-white rounded p-5">
        <button class="absolute top-4 right-4" @click="closeModal">X</button>
        <slot></slot>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ['isOpen'],
    methods: {
      closeModal() {
        this.$emit('close')
      }
    }
  }
  </script>
  