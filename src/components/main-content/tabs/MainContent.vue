<script setup>
import InformPlate from '@/components/main-content/tabs/main-tab-content/InformPlate.vue'
import HeroSection from '@/components/main-content/tabs/main-tab-content/HeroSection.vue'
import AboutRequests from '@/components/main-content/tabs/main-tab-content/AboutRequests.vue'
import UserProfile from '@/components/main-content/tabs/UserProfile.vue'
import SearchArea from '@/components/main-content/search/SearchArea.vue'
import UserSettings from '@/components/main-content/tabs/UserSettings.vue'
import SupportContacts from '@/components/main-content/tabs/SupportContacts.vue'

const props = defineProps({
    currentWindow: {
        type: String,
        required: true
    }
})

console.log(props.currentWindow)
</script>

<template>
    <div class="flex flex-col w-full mx-auto">
        <InformPlate v-if="currentWindow === 'Главная'" />
        <HeroSection v-if="currentWindow === 'Главная'" />
        <AboutRequests v-if="currentWindow === 'Главная'" />
        <UserProfile v-if="currentWindow === 'Профиль'" />
        <SearchArea v-if="currentWindow === 'Поиск тренера'" />
        <UserSettings v-if="currentWindow === 'Мои настройки'" />
        <SupportContacts v-if="currentWindow === 'Поддержка'" />
    </div>
</template>