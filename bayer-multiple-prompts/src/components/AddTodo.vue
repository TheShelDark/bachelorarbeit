<template>
  <div class="fixed inset-0 z-50 overflow-hidden flex items-center-center">
     <div class="absolute inset-0 overflow-hidden">
       <div class="absolute inset-0 bg-gray-500 bg-opacity-75 transition-opacity"></div>
       <section class="absolute inset-y-0 pl-16 max-w-full right-0 flex">
         <div class="w-screen max-w-md">
           <div class="h-full flex flex-col bg-white shadow-xl">
             <div class="px-4 py-2 bg-gray-200 flex justify-between items-center">
               <h2 class="text-lg font-black text-gray-800">Add a new Todo</h2>
               <button @click="close" class="text-600 hover:text-gray-800">
                 Close
               </button>
             </div>
             <form class="flex-grow flex flex-col justify-between p-6" @submit.prevent="submitForm">
               <label class="block font-bold text-gray-800 mb-2" for="title">
                 Title:
               </label>
               <input
                 class="border border-gray-400 p-2 w-full rounded-md mb-4"
                 id="title"
                 v-model="title"
                 type="text"
                 placeholder="Enter a title for the todo..."
                 required
               />
 
               <label class="block font-bold text-gray-800 mb-2" for="description">
                 Description:
               </label>
               <textarea
                 class="border border-gray-400 p-2 w-full rounded-md mb-4"
                 id="description"
                 v-model="description"
                 placeholder="Enter a description for the todo..."></textarea>
 
               <div>
                 <button
                   type="submit"
                   class="bg-blue-700 hover:bg-blue-600 text-white font-bold rounded-md py-2 px-4 w-full">
                   Add
                 </button>
               </div>
             </form>
           </div>
         </div>
       </section>
     </div>
   </div>
 </template>
 
 <script>
 export default {
   data() {
     return {
       title: '',
       description: '',
     }
   },
   methods: {
     submitForm() {
       const newTodo = { id: Date.now(), title: this.title, description: this.description };
       this.$emit('submit', newTodo);
       this.close();
     },
     close() {
       this.$emit('close');
     }
   }
 }
 </script>