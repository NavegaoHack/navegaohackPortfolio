<script setup>
const address = [
    {
        id: 1,
        type: "Gmail",
        val: "alejandro.cana.v",
        img: "https://www.svgrepo.com/show/535366/envelope.svg"
    },
    {
        id:2,
        type: "Location",
        val: "Nva. Esparta, Venezuela",
        img: "https://www.svgrepo.com/show/522167/location.svg"
    }
]

const svgs = [
    {
        id: 1,
        url: "https://www.svgrepo.com/show/501245/linkedin.svg"
    },
    {
        id: 2,
        url: "https://www.svgrepo.com/show/513089/youtube-168.svg"
    },
    {
        id: 3,
        url: "https://www.svgrepo.com/show/501210/github.svg"
    }


]
</script>

<template>
    <div class="flex flex-col gap-4 items-center rounded-xl  p-4 w-80 max-md:w-full">
        <img src="https://github.com/navegaohack.png" class="size-48 rounded-xl shadow-lg"/>
        <div>
            <h1 class="text-2xl font-bold text-center">NavegaoHack</h1>
            <p class="text-lg text-center text-gray-600">Not so professional software developer</p>
        </div>
        <div class="h-0.5 w-full bg-gray-300"></div>


        <div v-for="data in address" :key="data.id" class="w-full p-4 bg-gray-100 shadow-lg rounded-xl flex gap-2">

            <img class="size-12 p-2 dark:fill-sky-300" :src="data.img" alt="img"/>
            <div class="w-0.5 bg-gray-300"></div>
            <div>
            <h2 class="text-xl">{{data.type}}</h2>
            <p class="text-gray-600">{{data.val}}</p>
            </div>
        </div>

        <div class="flex gap-4">
            <img v-for="data in svgs" :key="data.id" class="size-4" :src="data.url"/>
        </div>


    </div>
</template>