<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const newValue = ref(null)

let theChart = null

const dataset = [
    300, 50, 100
]

const data = {
    labels: [
        "Red",
        "Blue",
        "Yellow"
    ],
    datasets: [
        {
            label: 'My first Dataset',
            data: dataset,
            backgroundColor: [
                'rgb(255,99,132)',
                'rgb(54,162,235)',
                'rgb(255,205,86)',
                'rgb(43,105,86)',
                'rgb(21,21,186)'
            ],
            hoverOffset: 4
        }
    ]
}

const config = {
    type: 'pie',
    data: data
}

onMounted(() => {
    const context = document.getElementById('myChart')
    theChart = new Chart(context, config)
})

onBeforeUnmount(() => {
    if (theChart) {
        theChart.destroy()
    }
})

function updateChart() {
    if (newValue.value) {
        dataset.push(newValue.value)
        theChart.data.datasets[0].data = dataset
        theChart.update()
    }
}




</script>

<template>
    <div class="w-[500px] h-[500px] border-gray-800 border p-2 mx-auto mb-5">
          <canvas id="myChart"></canvas>
    </div>

    <div class="flex items-center justify-center mb-10 p-3 shadow-lg bg-gray-100 mx-auto space-x-2">
        <input  class="px-3 py-1.5 focus:outline-none rounded-sm bg-white text-md text-gray-500 " v-model="newValue"
            type="text" placeholder="Input value">
        <button @click="updateChart()"  class="px-3 py-1.5 bg-blue-600 text-white border-none rounded-sm hover:bg-blue-800"
            type="submit">Add
            To Chart</button>
    </div>
</template>

<style scoped></style>