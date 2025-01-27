<script setup>
import { ref } from 'vue';

const socItems = ref([
    {
        id: 1,
        icon: '/src/assets/icons/in-icon.svg',
        link: 'https://linkedin.com'
    },
    {
        id: 2,
        icon: '/src/assets/icons/vk-icon.svg',
        link: 'https://vk.com'
    }

])
</script>

<template>
    <ul v-for="socItem in socItems" :key="socItem.id" class="flex items-center gap-3">
        <li v-bind:key="socItem.id" class="flex items-center">
            <a v-bind:href="`${socItem.link}`" target="_blank">
                <img :src="socItem.icon" class="w-full h-auto" alt="">
            </a>
        </li>
    </ul>
</template>