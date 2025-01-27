<script setup>
import { ref } from 'vue';
import HeaderLayout from '@/components/header/HeaderLayout.vue';
import MainLayout from '@/components/MainLayout.vue';
import FooterLayout from '@/components/footer/FooterLayout.vue';

const currentWindow = ref('Главная');

const setCurrentWindow = (namePage) => {
  currentWindow.value = namePage;
}
</script>

<template>
  <HeaderLayout :currentWindow="currentWindow" @update:modelValue="setCurrentWindow" />
  <MainLayout :currentWindow="currentWindow" @update:modelValue="setCurrentWindow" />
  <FooterLayout />
</template>