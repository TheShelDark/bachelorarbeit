<template>
    <div class="flex flex-row justify-center items-center gap-4">
        <h1 class="text-3xl font-bold">{{ text }}</h1>
        <i v-if="icon" class="fa-sharp fa-solid fa-list fa-2xl"></i>
    </div>
</template>

<script setup>
    const props = defineProps({
        text: String,
        icon: Boolean,
    })
</script>