<template>
  <div class="bg-white rounded-md shadow overflow-hidden flex justify-between items-center px-4 py-3 mb-4">
    <span class="text-lg">{{ todo.title }}</span>
    <div class="flex space-x-2">
      <button @click="$emit('edit')" class="border-2 rounded-md py-1 px-3 border-blue-500 text-blue-500 hover:bg-blue-500 hover:text-white transition-all duration-200 focus:outline-none focus:ring-2 focus:ring-blue-300 active:bg-blue-600">
        Edit
      </button>
      <button @click="$emit('remove')" class="border-2 rounded-md py-1 px-3 border-red-500 text-red-500 hover:bg-red-500 hover:text-white transition-all duration-200 focus:outline-none focus:ring-2 focus:ring-red-300 active:bg-red-600">
        Delete
      </button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  }
}
</script>