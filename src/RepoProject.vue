<script setup>
import { defineProps, onMounted, ref } from 'vue';
const props = defineProps(['project', 'readDesc'])


const getRawUrlContent = (path) => {
    return "https://raw.githubusercontent.com/" + path + "/refs/heads/main/public/default.jpg"
}

const chekRawUrl = async (path) => {
    try {
        const response = await fetch(getRawUrlContent(path), { method: 'HEAD' })
        return response.ok
    } catch {
        return false
    }
}

const thisProjectHasThumbnail = async () => {
    return await chekRawUrl(props.project.full_name)
}

const getThumbnail = () => {
    return getRawUrlContent(props.project.full_name)
}


const hasThumbnail = ref(false)

    // Projects.value.forEach(async Project => {
    //     Project.hasThumbnail = false
    //     Project.hasThumbnail = await chekRawUrl(Project.full_name)
    //     Project.thumbnail = getRawUrlContent(Project.full_name)
    // })

onMounted(async () => {
    hasThumbnail.value = await thisProjectHasThumbnail()
})


</script>

<template>
    <div
        class="w-80 h-72 p-4 bg-gray-200 hover:bg-gray-100 shadow-lg rounded-xl flex flex-col gap-2 hover:-translate-y-2 active:translate-y-2 transition-transform duration-300"
        @click="() => {
            props.readDesc(props.project.full_name)                
        }">
        <div class="h-2/3 overflow-hidden rounded-xl">
            <img v-if="hasThumbnail" :src="getThumbnail()" class="bg-cover bg-top">
            <div v-else class="h-full  text-4xl grid text-gray-500 place-content-center"> <p>{{ props.project.name }}</p> </div>
        </div>
        <h2 class="text-2xl font-bold">{{ props.project.name }}</h2>
        <p class="text-gray-700">{{ props.project.description }}</p>
    </div>
</template>