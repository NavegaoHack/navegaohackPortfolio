<script setup>
import { defineProps } from 'vue';
const props = defineProps(['info', 'viewable'])
const emit = defineEmits(['viewable'])

const closeReadme = () => {
    emit('viewable', { 'value': false })
}
</script>

<template>
    <div class="absolute top-0">

        <div :class="{'scale-100 opacity-100': props.viewable}" class="transition-all opacity-25 scale-75 duration-500 flex justify-center p-8 w-screen">
            <div v-if="props.viewable" class="w-2/3 bg-white shadow-2xl relative p-4 rounded-2xl">
                <div class="absolute select-none right-4 size-4 grid place-content-center p-4 rounded-full bg-gray-400 text-white hover:scale-110 active:bg-gray-300" @click="closeReadme">x</div>
                <div class="flex flex-col gap-4 p-4 repo-description" v-html="props.info">

                </div>
            </div>
        </div>

    </div>
</template>