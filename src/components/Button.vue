<script setup>
const props = defineProps({
    label: {
        type: String,
        default: 'Hello World!'
    },
    color: {
        type: String,
        default: 'blue'
    }
})

function getColor() {
    return ` bg-${props.color}-800  hover:bg-${props.color}-400`
}
</script>

<template>
    <button :class="getColor()" class="px-6 py-3 text-white font-bold hover:text-black rounded-md">
        {{ props.label }}
    </button>
</template>

<style scoped></style>