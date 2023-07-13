<template>
    <div id="modal-backdrop" 
        style="background-color: rgba(0, 0, 0, 0.3);" 
        class="fixed top-0 left-0 right-0 bottom-0 flex justify-center items-center"
        @keyup.esc="$emit('close')"
    >
      <div id="modal" class="bg-white shadow-xl rounded-xl flex flex-col overflow-x-auto px-4">
        <header id="modal-header" class="p-6 flex relative border-b-1 justify-between">
                <h1 class="font-bold text-2xl underline">{{ title }}</h1>
            <button
                type="button"
                id="btn-close"
                class="absolute top-0 right-0  cursor-pointer font-bold bg-transparent text-xl"
                @click="$emit('close')"
            >
                x
            </button>
        </header>

        <section id="modal-body" class="relative py-5 px-4">
            <slot />
        </section>

      </div>
    </div>
</template>

<script setup>
    const props = defineProps({
        title: String,
    })
</script>