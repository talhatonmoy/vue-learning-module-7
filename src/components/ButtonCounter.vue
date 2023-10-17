<script setup>
import Button from './Button.vue'
import { ref } from 'vue'

const count = ref(1)

function increase() {
    count.value++
}

function decrease() {
    count.value--
}
</script>

<template>
    <div class=" flex justify-between items-center w-[300px]">
        <Button @Click="decrease()" label="-" color="green" />
        <p>{{ count }}</p>
        <Button @Click="increase()" label="+" color="red" />
    </div>
</template>

<style scoped></style>