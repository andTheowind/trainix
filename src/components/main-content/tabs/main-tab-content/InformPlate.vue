<script setup>
import { ref, onMounted } from 'vue';
const userName = ref('');
const isVisible = ref(true);

const updateUserName = () => {
    const storedUserInfo = localStorage.getItem('userInfo');
    if (storedUserInfo) {
        const { name, surname } = JSON.parse(storedUserInfo);
        userName.value = `${surname} ${name}`;
    }
}

window.addEventListener('storage_userInfo', () => {
    updateUserName();
})

onMounted(() => {
    updateUserName();
})

const hideBlock = () => {
    isVisible.value = false;
}
</script>

<template>
    <div v-if="isVisible"
        class="flex gap-8 items-center bg-[#1E1E2D] rounded-[100px] relative py-5 px-10 max-w-3xl mx-auto mt-4">
        <div>
            <img src="/src/assets/icons/important-icon.svg" class="max-w-full h-auto">
        </div>
        <div class="text-[#8D8BA2] text-sm">
            Добро пожаловать, {{ userName }}! Для ознакомления с возможностями сервиса
            посмотрите ознакомительные
            <a href="https://www.youtube.com/watch?v=IY2j_GPIqRA" target="_blank" class="text-[#7AB0FF] font-semibold">
                видео
            </a>
        </div>
        <a href="#" @click="hideBlock" class="absolute top-8 right-9">
            <img src="/src/assets/icons/close-btn.svg" alt="">
        </a>
    </div>
</template>