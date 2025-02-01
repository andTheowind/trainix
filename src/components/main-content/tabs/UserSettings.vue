<script>

export default {
    data() {
        return {
            langs: [{
                code: 'ru', name: 'Русский', icon: {
                    src: new URL('@/assets/icons/russia-lang.png', import.meta.url).href,
                    alt: 'Russian Flag'
                }
            }, {
                code: 'en', name: "English", icon: {
                    src: new URL('@/assets/icons/english-lang.png', import.meta.url).href,
                    alt: 'English Flag'
                }
            }],
            isDropdownLangVisible: false,
            selectedLang: localStorage.getItem('selectedLang') || 'Русский',
            timeNow: new Date().toLocaleTimeString('ru-RU', { hour: 'numeric', minute: 'numeric' }),
        }
    },
    methods: {
        toggleDropdownLang() {
            this.isDropdownLangVisible = !this.isDropdownLangVisible;
        },

        selectLang(lang) {
            this.selectedLang = lang;
            localStorage.setItem('selectedLang', lang);
            this.isDropdownLangVisible = false;
        }
    },
    computed: {
        currentFlagPath() {
            const langToFlagMap = {
                'Русский': 'russia-lang.png',
                'English': 'english-lang.png',
            }
            return `/src/assets/icons/${langToFlagMap[this.selectedLang] || 'default-lang.png'}`;
        }
    }
}


</script>

<template>
    <div class="flex flex-col bg-[#1C1C2E] rounded-3xl py-8 px-12 mt-4">
        <div class="flex items-center gap-4 mb-4">
            <img src="@/assets/icons/settings-icon.svg" alt="Settings Icon" class="w-6 h-6">
            <h2 class="text-[#FEFEFE] text-xl font-semibold">Настройки</h2>
        </div>
        <hr class="border-[#3A3A4A] my-4">

        <!-- Секция выбора языка -->
        <div>
            <div class="relative">
                <!-- Текущий выбранный язык -->
                <div class="flex items-center gap-4 cursor-pointer py-3 rounded-lg transition-all duration-200"
                    @click="toggleDropdownLang">
                    <p class="text-[#B4B4C4] text-lg pe-8">Язык</p>
                    <div>
                        <img :src="currentFlagPath" :alt="selectedLang" class="w-6 h-6 rounded-full">
                    </div>
                    <img src="@/assets/icons/arrow-down.svg" class="w-5 h-5 transition-transform duration-200"
                        :class="{ 'rotate-180': isDropdownLangVisible }">
                </div>

                <!-- Выпадающий список -->
                <div v-if="isDropdownLangVisible"
                    class="absolute left-0 top-full mt-2 bg-[#1E1E2D] rounded-lg shadow-lg py-2 min-w-[200px] z-10">
                    <ul class="list-none p-0 m-0">
                        <li v-for="item in langs" :key="item.code" @click="selectLang(item.name)"
                            class="hover:bg-[#3A3A4A] cursor-pointer">
                            <div
                                class="flex items-center gap-3 px-4 py-2 text-[#92929F] hover:text-white transition-colors">
                                <img :src="item.icon.src" :alt="item.icon.alt"
                                    class="w-5 h-5 rounded-full">
                                <span class="text-sm">{{ item.name }}</span>
                            </div>
                        </li>
                    </ul>
                </div>
            </div>

            <div>
                <div class="flex items-center gap-4 py-3 rounded-lg transition-all duration-200">
                    <p class="text-[#B4B4C4] text-lg pe-4">Время</p>
                    <p class="text-[#FEFEFE] text-lg font-semibold">{{ timeNow }}</p>
                </div>
            </div>
        </div>
    </div>
</template>
