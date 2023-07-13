<script setup>
    const props = defineProps({
        todo: Object,
    })
</script>

<template>
    <li class="flex flex-row items-center justify-between gap-6 rounded-lg bg-neutral-200 mb-4 md:mr-4 md:mt-0 mt-4 p-4 px-2">
        <div class="flex flex-col">
            <h1 class="font-bold text-lg">{{ todo.title }}</h1>
            <p class="text-base hidden md:block">{{ todo.description }}</p>
        </div>
        <div>
            <i @click="$emit('edit', todo)" class="fa-solid fa-pen-to-square fa-xl mr-4 cursor-pointer"></i>
            <i @click="$emit('delete')" class="fa-solid fa-trash fa-xl cursor-pointer" style="color: #ff0000;"></i>
        </div>
    </li>
</template>