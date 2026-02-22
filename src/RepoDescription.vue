<script setup>
import { defineProps } from 'vue';
const props = defineProps(['info'])
</script>

<template>
    <div class="absolute translate-x-4 translate-y-4">

        <div class="size-4 grid place-content-center p-4 rounded-full bg-gray-400 text-white">x</div>
        <div class="w-2/3 bg-white shadow-2xl flex flex-col gap-4 p-4 repo-description" v-html="props.info">

        </div>

    </div>
</template>