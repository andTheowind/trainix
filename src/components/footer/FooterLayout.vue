<script setup>
import FooterNav from '@/components/footer/FooterNav.vue';
import FooterSoc from '@/components/footer/FooterSoc.vue';
</script>

<template>
    <footer class="bg-[#1E1E2D] flex w-full mx-auto">
        <div class="max-w-[1440px] flex justify-between mx-auto w-full px-5 py-8 gap-x-6">
            <div class="flex items-center gap-x-4">
                <span class="block text-[#8D8BA2]">andTheowind © 2025</span>
            </div>
            <div class="flex items-center gap-x-3">
                <FooterNav />
                <FooterSoc />
            </div>
        </div>
    </footer>
</template>