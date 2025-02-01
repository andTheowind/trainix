<script>
import HeaderLayout from '@/components/header/HeaderLayout.vue';
import MainLayout from '@/components/MainLayout.vue';
import FooterLayout from '@/components/footer/FooterLayout.vue';

export default {
  components: {
    HeaderLayout,
    MainLayout,
    FooterLayout
  },
  data() {
    return {
      currentWindow: 'Главная'
    }
  },
  methods: {
    setCurrentWindow(namePage) {
      this.currentWindow = namePage;
    }
  }
}
</script>

<template>
  <header-layout :currentWindow="currentWindow" @updateWindow="setCurrentWindow" />
  <main-layout :currentWindow="currentWindow" @updateWindow="setCurrentWindow" />
  <footer-layout />
</template>
