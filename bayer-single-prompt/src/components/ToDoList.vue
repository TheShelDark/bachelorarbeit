<template>
<div class="rounded-md bg-gray-100-4">
    <div class="mb-4">
      <!-- Button -->
      <button
        class="bg-blue-500 hover:bg-blue600 text-white font-bold py-2 px-4 rounded"
        @click="$emit('open-add-todo')"
      >
        Add ToDo
      </button>
    </div>
    <!-- List View -->
    <ul class="space-y-4">
      <li v-for="(todo, index) in todos" :key="index">
        <div class="bg-white p-4 rounded-md">
          <div class="flex justify-between items-center">
            <h2 class="text-lg font-bold">{{ todo.title }}</h2>
            <div>
              <!-- Edit Button -->
              <button
                class="bg-green-500 hover:bg-green-600 text font-bold py-2 px-3 rounded mr-2"
                @click="$emit('open-edit-todo', todo)"
              >
                Edit
              </button>
              <!-- Delete Button -->
              <button
                class="bg-red-500 hover:bg-red-600 text-white font-bold py-2 px-3 rounded"
                @click="$emit('delete-todo', todo.id)"
              >
                Delete
              </button>
            </div>
          </div>
          <p class="text-gray-700">{{ todo.description }}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    todos: {
      type: Array,
      required: true
    }
  }
};
</script>