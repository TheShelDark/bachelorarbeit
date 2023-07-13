<template>
    <div id="modal-backdrop" style="background-color: rgba(0, 0, 0, 0.3);" class="fixed top-0 left-0 right-0 bottom-0 flex justify-center items-center">
      <div id="modal" class="bg-white shadow-xl rounded-xl flex flex-col overflow-x-auto px-4">
        <header id="modal-header" class="p-6 flex relative border-b-1 justify-between">
            <slot name="header">
                <h1 class="font-bold text-2xl underline">Edit your Todo</h1>
            </slot>
            <button
                type="button"
                id="btn-close"
                class="absolute top-0 right-0  cursor-pointer font-bold bg-transparent text-xl"
                @click="closeModal"
            >
                x
            </button>
        </header>

        <section id="modal-body" class="relative py-5 px-4">
            <slot name="body">
                <form class="flex flex-col">
                    <label for="title-input">Enter your Title:</label>
                    <input id="title-input" v-model="todo.title" class="rounded border my-4 p-2" type="text" placeholder="Todo Title" />
                    <label for="description-input">Enter your Description:</label>
                    <textarea id="description-input" v-model="todo.description" class="rounded border my-4 p-2" type="text" placeholder="Todo Description" />
                </form>
            </slot>
        </section>

        <footer id="modal-footer" class="p-4 flex border-t-1 flex-col justify-end">
            <slot name="footer">
                
            </slot>
            <button
                type="button"
                id="btn-green"
                class="text-white bg-lime-400 border-1 rounded-lg"
                @click="closeModal"
            >
                Edit Todo
            </button>
        </footer>
      </div>
    </div>
  </template>

  <script>
    export default {
        name: "EditTodoModal",
        props: {
            todo: Object,
        },
        methods: {
            closeModal() {
                this.$emit('close')
            },
        },
        data() {
            return {
                /*todo_title: todo.title,
                todo_description: todo.description*/
            }
        },
        
    }
  </script>