<template>
  <div class="bg-white shadow p-4 rounded-lg my-4 flex justify-between">
    <div class="mr-4">
      <h2 class="text-xl">{{ todo.title }}</h2>
      <p class="hidden lg:block">{{ todo.description }}</p> <!-- Description is hidden on screens smaller than lg -->
    </div>
    <div class="self-center">
      <button @click="$emit('edit-todo', todo)" class="mr-2 bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Edit</button>
      <button @click="$emit('delete-todo', todo)" class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-4 rounded">Delete</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ['todo']
}
</script>
