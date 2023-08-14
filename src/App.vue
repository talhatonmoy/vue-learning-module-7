<script setup>
import { ref, onMounted, nextTick, onBeforeUnmount } from 'vue'


let slider = null
const newImage = ref(null);


const images = ref([
    "https://cdn.pixabay.com/photo/2014/09/14/18/04/dandelion-445228_1280.jpg",
    "https://cdn.pixabay.com/photo/2014/04/14/20/11/pink-324175_1280.jpg",
    "https://cdn.pixabay.com/photo/2012/03/01/00/55/flowers-19830_1280.jpg",
    "https://cdn.pixabay.com/photo/2013/07/21/13/00/rose-165819_1280.jpg"

])


onMounted(() => {
    slider = new Flickity('.carousel', {
        wrapAround: true
    });
})



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

onBeforeUnmount(() => {
    slider.destroy()
})


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
        <div class="carousel parent-div mx-auto">
            <div v-for="img, index in images" :key="index" :style="`background:url(${img})`"
                class=" w-[650px] h-[450px] bg-contain mx-auto bg-center "></div>
        </div>
    </div>
</template>

<style scoped>
.parent-div {
    width: 600px;
    height: 400px;
}

.parent-div div {
    width: 600px;
    height: 400px;
    background-color: #ccc;

}
</style>