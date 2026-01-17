<script setup>
const skillUrl = (i) => {
        return `/public/skill_${i % 8 + 1}.svg`
    }
</script>

<template>
    <div class="flex gap-4 animate-slide">
        <img v-for="i in 24" :key="i" class="size-16" :src=skillUrl(i) alt="">
    </div>
</template>