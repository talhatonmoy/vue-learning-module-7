<script setup>
import { ref, onMounted } from 'vue'


const images = ref([
    "https://images.unsplash.com/photo-1691523103943-d48a90280dd2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2940&q=80",
    "https://images.unsplash.com/photo-1691380302078-3d0a8b5fe52d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80",
    "https://images.unsplash.com/photo-1675725399060-b638b1c15b50?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1674&q=80",
    "https://images.unsplash.com/photo-1688643188950-dcc91eea00de?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80",
    "https://images.unsplash.com/photo-1691249238710-8ee787d4fd0a?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=2070&q=80"
])

const newImage = ref(null);

//initializing carousel
onMounted(() => {
    const slider = new Flickity('.carousel', {});
})

</script>

<template>
    <div class="container dark:bg-white h-screen p-3">
        <div class="w-[1200px] ">
            <div class="flex items-center justify-center mb-10 p-3 shadow-lg bg-gray-100 mx-auto space-x-2">
                <input v-model="newImage" class="px-3 py-1.5 focus:outline-none rounded-sm bg-white text-md text-gray-500 " type="text"
                    placeholder="Input Image Url">
                <button @click="images.push(newImage)" class="px-3 py-1.5 bg-blue-600 text-white border-none rounded-sm hover:bg-blue-800" type="submit">Add
                    Image</button>
            </div>
        </div>

        <div class="w-1/2 mx-auto">
            <div class="carousel" data-flickity='{ "wrapAround": true }'>
                <div v-for="(img, index) in images" :key="index"> <img class="w-full h-fit" :src="img" alt=""></div>
            </div>
        </div>
    </div>
</template>

<style scoped>




</style>