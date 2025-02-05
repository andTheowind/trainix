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
  <HeaderLayout :currentWindow="currentWindow" @updateWindow="setCurrentWindow" />
  <MainLayout :currentWindow="currentWindow" @updateWindow="setCurrentWindow" />
  <FooterLayout />
</template>
