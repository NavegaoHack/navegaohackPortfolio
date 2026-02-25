<script setup>
import { marked } from 'https://cdn.jsdelivr.net/npm/marked/lib/marked.esm.js';
import { onMounted, ref } from 'vue';
import RepoDescription from './RepoDescription.vue';
import Sidebar from './Sidebar.vue';
import RepoProject from './RepoProject.vue';


const repoDescriptionText = ref("")
const isRepoDescriptionViewable = ref(false)


const getReadmeFile = (path) => {
    const url = "https://raw.githubusercontent.com/" + path + "/refs/heads/main/README.md"

    fetch(url)
        .then(res => {
            if (!res.ok) throw new Error("## Sorry, has not a README yet :(")
            return res
        })
        .then(res => res.text())
        .then(text => {
            repoDescriptionText.value = marked.parse(text)
            console.log(text)
            isRepoDescriptionViewable.value = true
        })
        .catch(err => {
            console.log(err)
            repoDescriptionText.value = marked.parse(err.message)
            isRepoDescriptionViewable.value = true
        })
}


const Projects = ref([])

onMounted(async() => {
    const response = await fetch("https://api.github.com/users/navegaohack/repos")
    Projects.value = await response.json()

    Projects.value = Projects.value.filter((project) => {return project.id !== 1136249970}) //substract the navegaohack.github.io dist

    //adding default test for description popup
    repoDescriptionText.value = marked.parse('# Hello World')


})

</script>

<template>
    <div class="relative">
        <div class="flex p-4 gap-4 items-start justify-center max-md:flex-col max-md:items-center transition-opacity duration-700" :class="{'opacity-50': isRepoDescriptionViewable}">
            <Sidebar/>
            <main class="p-4  bg-gray-100 w-2/3 max-md:w-full rounded-xl">
                <h3 class="text-3xl text-center font-bold mb-4">Projects</h3>
                <div class="flex flex-wrap justify-center gap-4">
                    <RepoProject v-for="Project in Projects" :key="Project.id" :project="Project" :readDesc="getReadmeFile"/>
                </div>
                
            </main>


        </div>
        <RepoDescription @viewable="(r) => {isRepoDescriptionViewable = r.value}" :viewable="isRepoDescriptionViewable" :info="repoDescriptionText"/>
    </div>


</template>