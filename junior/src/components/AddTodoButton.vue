<template>
    <button @click="clickfunc" class="py-2 px-4 rounded-lg bg-lime-400 hover:bg-lime-200 hover:cursor-pointer">
        Add Todo 
        <i class="fa-solid fa-plus fa-lg ml-2" style="color: #000000;"></i>    
    </button>
</template>

<script>
    export default {
        name: "AddTodoButton",
        props: {
            clickfunc: Function,
        }
    }
</script>