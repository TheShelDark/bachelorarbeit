<template>
    <div>
        <div :key="todo.id" v-for="todo in todos" class="">
            <Todo 
                :deleteTodo="removeFunc" 
                :todo="todo" 
                @onEdit="$emit('editFunc')"
            />
        </div>
    </div>
</template>

<script>
    import Todo from './Todo.vue';

    export default {
        name: "TodoList",
        props: {
            todos: Array,
            removeFunc: Function,
        },
        components: {
            Todo,
        },
    }
</script>