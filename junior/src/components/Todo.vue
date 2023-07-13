<template>
    <div class="flex flex-row items-center justify-between gap-6 rounded-lg bg-neutral-100 mb-4 md:mr-4 md:mt-0 mt-4 p-4 px-2">
        <div class="flex flex-col">
            <h1 class="font-bold text-lg">{{ todo.title }}</h1>
            <p class="text-base hidden md:block">{{ todo.description }}</p>
        </div>
        <div class="">
            <i @click="showEditModal" class="fa-solid fa-pen-to-square fa-xl mr-4 cursor-pointer"></i>
            <i @click="deleteTodo(todo.id)" class="fa-solid fa-trash fa-xl cursor-pointer" style="color: #ff0000;"></i>
        </div>
        <EditTodoModal 
            v-show="isEditModalVisible"
            :todo="todo"
            @onEdit="$emit('onEdit')"
            @close="closeEditModal"
        />
    </div>
</template>

<script>
    import EditTodoModal from './EditTodoModal.vue';

    export default {
        name: "Todo",
        props: {
            todo: Object,
            deleteTodo: Function,
        },
        components: {
            EditTodoModal,
        },
        data() {
            return {
                isEditModalVisible: false,
            }
        },
        methods: {
            showEditModal() {
                this.isEditModalVisible = true;
            },
            closeEditModal() {
                this.isEditModalVisible = false;
            },
        }
    }
</script>