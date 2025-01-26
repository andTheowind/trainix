<script setup>

</script>

<template>
    <div class="flex flex-col bg-[#1C1C2E] rounded-3xl py-8 px-12 mt-4">
        <div class="flex items-center gap-4 mb-4">
            <img src="@/assets/icons/help-icon.svg" alt="Support Icon" class="w-6 h-6">
            <h2 class="text-[#FEFEFE] text-xl font-semibold">Связь с поддержкой</h2>
        </div>
        <hr class="border-[#3A3A4A] my-4">
        <div>
            <div class="flex items-center gap-4 py-3 rounded-lg transition-all duration-200">
                <p class="text-[#B4B4C4] text-lg pe-4">Почта</p>
                <a href="mailto:and.theowind@gmail.com"
                    class="block text-[#FEFEFE] text-lg font-semibold hover:underline">
                    and.theowind@gmail.com
                </a>
            </div>
            <div class="flex items-center gap-4 py-3 rounded-lg transition-all duration-200">
                <p class="text-[#B4B4C4] text-lg pe-4">Телеграм</p>
                <a href="https://t.me/andtheowind" class="block text-[#FEFEFE] text-lg font-semibold hover:underline">
                    @andtheowind
                </a>
            </div>
        </div>
    </div>
</template>