<script setup>
import Contact from './Contact.vue';
import Hr from './Hr.vue';
import Resume from './Resume.vue';
import TechCarousel from './TechCarousel.vue';

</script>

<template>
    <div class="w-1/3  p-4 bg-slate-200 rounded-xl">
        
        <h1 class="text-4xl font-bold">Proyectos Destacados</h1>
        <Hr/>
        
        <div class="grid grid-cols-2 gap-4 my-4">
            <div v-for="i in 5" :key="i" class="border-2 w-full h-36"></div>

        </div>
        
        <h2 class="my-4 text-3xl font-bold">Tecnologías</h2>
        <Hr/>
        
        <div class="overflow-hidden">
            <TechCarousel/>
        </div>

        <h2 class="my-4 text-3xl font-bold">Hoja de Vida</h2>
        <Hr/>

        <Resume/>

        <h2 class="my-4 text-3xl font-bold">Contacto</h2>
        <Hr/>

        <Contact/>

    </div>
</template>   