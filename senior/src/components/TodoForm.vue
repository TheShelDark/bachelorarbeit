<script setup>
    import Button from './Button.vue';
    import { ref } from "vue"

    const props = defineProps({
        todo: {
            type: Object,
            required: false,
        }
    })
    
    const todoToSave = ref({...props.todo})

</script>

<template>
    <form v-if="todo" class="flex flex-col" @submit.prevent="$emit('save', todoToSave)">
        <label for="title-input">Enter your Title:</label>
        <input id="title-input" v-model="todoToSave.title" class="rounded border my-4 p-2" type="text" placeholder="Todo Title" />
        <label for="description-input">Enter your Description:</label>
        <textarea id="description-input" v-model="todoToSave.description" class="rounded border my-4 p-2" type="text" placeholder="Todo Description" />
        <Button 
            text="Save Todo"
            type="submit"
        />
    </form>
</template>