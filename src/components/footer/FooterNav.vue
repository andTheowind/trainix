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
</script>

<template>
    <nav class="flex items-center gap-x-4 text-[#8D8BA2]" v-for="navPage in navPages" :key="navPage.id">
        <a href="#" class="block">{{ navPage.title }}</a>
    </nav>
</template>