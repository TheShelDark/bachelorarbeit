<template>
    <div class="md:grid md:grid-cols-2 items-start gap-4 flex flex-col-reverse mt-6 border-2 rounded-lg p-6">
        <TodoList 
            :todos="todos" 
            :removeFunc="removetodo" 
            @editFunc="$emit('on-edit')"
        />
        <AddTodoButton :clickfunc="onaddclick" />
    </div>
</template>

<script>
    import TodoList from './TodoList.vue';
    import AddTodoButton from './AddTodoButton.vue';

    export default {
        name: "TodoContainer",
        props: {
            todos: Array,
            onaddclick: Function,
            removetodo: Function,
        },
        components: {
            TodoList,
            AddTodoButton,
        },

    }
</script>