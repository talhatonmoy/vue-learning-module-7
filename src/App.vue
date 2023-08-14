<script setup>
import { ref, onMounted, nextTick, onBeforeMount } from 'vue'


const images = ref([
    "https://plus.unsplash.com/premium_photo-1675804669860-9e27f22b0681?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1650&q=80",
    "https://images.unsplash.com/photo-1537346439163-eafb59bdc400?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1374&q=80",
    "https://plus.unsplash.com/premium_photo-1675448891094-1c3899f6f67a?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1470&q=80",
    "https://images.unsplash.com/photo-1539634262233-7c0b48ab9503?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1425&q=80",
])


// const images = ref([
//     'img/1.avif',
//     'img/2.avif',
//     'img/3.avif',
//     'img/4.avif',
// ])

onMounted(() => {
    slider = new Flickity('.carousel', {
        wrapAround: true
    });
})

const newImage = ref(null);
let slider = null

function addNewImage() {
    if (newImage.value) {
        images.value.push(newImage.value)
        slider.destroy()
        nextTick(() => {
            slider = new Flickity('.carousel', {
                wrapAround: true
            });
        })
        newImage.value = ''
    }
    
}


</script>

<template>
    <div class="container dark:bg-white min-h-screen p-3">
        <div class="w-[1200px] ">
            <div class="flex items-center justify-center mb-10 p-3 shadow-lg bg-gray-100 mx-auto space-x-2">
                <input v-model="newImage" class="px-3 py-1.5 focus:outline-none rounded-sm bg-white text-md text-gray-500 "
                    type="text" placeholder="Input Image Url">
                <button @click="addNewImage()"
                    class="px-3 py-1.5 bg-blue-600 text-white border-none rounded-sm hover:bg-blue-800" type="submit">Add
                    Image</button>
            </div>
        </div>
        <p>{{ newImage }}</p>
        <div class="carousel">
            <div v-for="img, index in images" :key="index" :style="`background:url(${img})`" class=" w-[650px] h-[450px] bg-contain mx-auto bg-center "></div>
        </div>
    </div>
</template>

<style scoped></style>