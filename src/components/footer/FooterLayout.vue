<script setup>
import { ref } from 'vue';

const navPages = ref([
    {
        id: 1,
        title: 'Политика конфиденциальности'
    },
    {
        id: 2,
        title: 'Контакты'
    },
    {
        id: 3,
        title: 'Ещё'
    }
])

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
    <footer class="bg-[#1E1E2D] flex w-full mx-auto">
        <div class="max-w-[1440px] flex justify-between mx-auto w-full px-5 py-8 gap-x-6">
            <div class="flex items-center gap-x-4">
                <span class="block text-[#8D8BA2]">andTheowind © 2025</span>
            </div>
            <div class="flex items-center gap-x-3">
                <nav class="flex items-center gap-x-4 text-[#8D8BA2]" v-for="navPage in navPages" :key="navPage.id">
                    <a href="#" class="block">{{ navPage.title }}</a>
                </nav>
                <ul v-for="socItem in socItems" :key="socItem.id" class="flex items-center gap-3">
                    <li v-bind:key="socItem.id" class="flex items-center">
                        <a v-bind:href="`${socItem.link}`" target="_blank">
                            <img :src="socItem.icon" class="w-full h-auto" alt="">
                        </a>
                    </li>
                </ul>
            </div>
        </div>
    </footer>
</template>