<script setup>
import Hr from './Hr.vue';

const contacts = [
    {   
        i: 1,
        type: "Email",
        value: "NavegaoHack@gmail.com"
    },
    {
        i: 2,
        type: "Phone",
        value: "+123 456 7890"
    },
    {
        i: 3,
        type: "Location",
        value: "Nva Esparta. Venezuela"
    },  
]

const addressImgUrl = (i) => {return `/public/address_${i}.svg`}

</script>

<template>
    <div class="w-72 bg-slate-200 p-4 flex flex-col items-center rounded-xl">
        <!--Main Greeting-->

        <img class="size-36 mb-2 rounded-xl" src="https://github.com/navegaohack.png"/>
        <h1 class="text-3xl font-bold">NavegaoHack</h1>
        <h2 class="text-xl text-center">Not so profesional web developer</h2>
        
        <Hr/>
        
        <!--Contact addresses-->

        <div class="flex flex-col gap-4">
            <div class="flex gap-2" v-for="contact in contacts" :key="contact.type">
                <img class="size-12" :src=addressImgUrl(contact.i) alt="">
                <div>
                    <h3 class="text-lg font-bold">{{ contact.type }}</h3>
                    <p class="text-md">{{ contact.value }}</p>
                </div>
            </div>

        </div>

        <!--Social Media-->
        <div class="my-4 flex gap-2">
            <img v-for="i in 4" :key="i" class="size-4" src="/public/skill_2.svg" alt="social media">
        </div>

    </div>
</template>