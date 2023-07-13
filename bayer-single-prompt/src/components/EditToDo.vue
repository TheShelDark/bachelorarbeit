<template>
    <div class="fixed inset-0 z-10 overflow-y-auto">
        <div class="flex items-center justify-center min-h-screen">
            <div class="fixed inset-0 transition-opacity">
                <div class="absolute inset-0 bg-gray-500 opacity-75"></div>
            </div> <!-- Pop-Up -->
            <div class="bg-white rounded-md overflow-hidden w-96 fixed">
                <div class="p-4">
                    <h2 class="text-lg font-bold mb-4">Edit ToDo</h2>
                    <form @submit.prevent="onSubmit">
                        <div class="mb-4"> <label class="block text-gray-700 font-bold mb-2" for="title"> Title </label>
                            <input
                                class="appearance-none border rounded w-full py-2 px-3 text-gray700 leading-tight focus:outline-none focus:shadow-outline"
                                id="title" v-model="form.title" type="text" required />
                        </div>
                        <div class="mb-4"> <label class="block text-gray-700 font-bold mb-2" for="description"> Description
                            </label> <textarea
                                class="appearance-none border rounded w-full py-2 px-3 text-gray700 leading-tight focus:outline-none focus:shadow-outline"
                                id="description" v-model="form.description" required></textarea> </div>
                        <div class="flex justify-end"> <!-- Save Button --> <button
                                class="bg-blue-500 hover:bg-blue-600 text-white font-bold py-2 px-4 rounded mr-2"
                                type="submit"> Save </button> <!-- Cancel Button --> <button
                                class="bg-gray-500 hover:bg-gray-600 text-white font-bold py-2 px-4 rounded"
                                @click="$emit('close-edit-todo')"> Cancel </button> </div>
                    </form>
                </div>
            </div>
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
    },
    data() {
      return {
        form: {
          title: this.todo.title,
          description: this.todo.description
        }
      };
    },
    methods: {
      onSubmit() {
        this.$emit("edit-todo", {
          id: this.todo.id,
          title: this.form.title,
          description: this.form.description
        });
      }
    }
  };
  </script>