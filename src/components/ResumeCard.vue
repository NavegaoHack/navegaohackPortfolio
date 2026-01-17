<script setup>
defineProps({
    name: String,
    desc: String,
    date: String,
    })
</script>

<template>
    <div class="flex gap-4">
        <div class="size-3 mt-2 rounded-full bg-amber-400"></div>
        <div>
            <h1 class="text-lg">{{ name }}</h1>
            <h2 class="text-base text-black/75">{{ desc }}</h2>
            <h3 class="text-base text-black/50">{{ date }}</h3>
        </div>
    </div>

</template>