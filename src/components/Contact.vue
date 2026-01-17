<script setup>

</script>

<template>
    <div class="flex flex-col gap-6">
        <div class="flex  justify-between gap-6">
            <input class="border-slate-500 border rounded-xl w-full h-12 px-4" type="text" placeholder="Nombre">
            <input class="border-slate-500 border rounded-xl w-full h-12 px-4" type="text" placeholder="Apellido">
        </div>
        <input class="border-slate-500 border rounded-xl w-full h-12 px-4" type="text" placeholder="Asunto">
        <textarea class="border-slate-500 border rounded-xl w-full h-48 p-4" name="" id="" placeholder="Mensaje"></textarea>
        <button class="p-4 rounded-lg bg-purple-600 text-white">Enviar</button>
    </div>
</template>