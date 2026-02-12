<script setup>
import { onMounted, ref } from 'vue';


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

const getRawUrlContent = (path) => {
    return "https://raw.githubusercontent.com/" + path + "/refs/heads/main/public/default.jpg"
}

const chekRawUrl = async (path) => {
    try {
        const response = await fetch(getRawUrlContent(path), { method: 'HEAD' })
        console.log(response.ok)
        return response.ok
    } catch {
        return false
    }
}

const Projects = ref([])

onMounted(async() => {
    const response = await fetch("https://api.github.com/users/navegaohack/repos")
    Projects.value = await response.json()

    //adding thumbnail

    Projects.value.forEach(async Project => {
        Project.hasThumbnail = await chekRawUrl(Project.full_name)
        Project.thumbnail = getRawUrlContent(Project.full_name)
    })
})

</script>

<template>
    <div class="flex gap-4 p-4 items-start justify-center max-md:flex-col max-md:items-center">
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
                <img class="size-4" src="https://www.svgrepo.com/show/501245/linkedin.svg"/>
                <img class="size-4" src="https://www.svgrepo.com/show/513089/youtube-168.svg"/>
                <img class="size-4" src="https://www.svgrepo.com/show/501210/github.svg"/>
            </div>


        </div>
        <main class="p-4  bg-gray-100 w-2/3 max-md:w-full rounded-xl">
            <h3 class="text-3xl text-center font-bold mb-4">Projects</h3>
            <div class="flex flex-wrap justify-center gap-4">
                <div v-for="Project in Projects" :key=Project.id class="w-80 h-72 p-4 bg-gray-200 shadow-lg rounded-xl flex flex-col gap-2">
                    <div class="h-2/3 overflow-hidden rounded-xl">
                        <img v-if="Project.hasThumbnail" :src="getRawUrlContent(Project.full_name)" alt="" class="bg-cover bg-top">
                        <div v-else class="h-full  text-4xl grid text-gray-500 place-content-center"> <p>{{ Project.name }}</p> </div>
                    </div>
                    <h2 class="text-2xl font-bold">{{ Project.name }}</h2>
                    <p class="text-gray-700">{{ Project.description }}</p>
                </div>
            </div>
            
        </main>
    </div>

</template>