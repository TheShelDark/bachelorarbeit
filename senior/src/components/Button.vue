<template>
    <button
        class="py-2 px-4 rounded-lg bg-lime-400 hover:bg-lime-200 hover:cursor-pointer"
        @click="$emit('click')"
    >
        {{ text }}
    </button>
</template>

<script setup>
    const props = defineProps({
        text: String,
    })
</script>