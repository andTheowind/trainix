<script setup>
import { ref } from 'vue';
import getCoachData from '@/Data';

const positionIcons = {
    Вратарь: '/src/assets/img/goalkeeper.svg',
    Защитник: '/src/assets/img/defender.svg',
    Форвард: '/src/assets/img/forward.svg',
    Полузащитник: '/src/assets/img/midfielder.svg',
};

const getIcon = (position) => {
    return positionIcons[position] || '/src/assets/icons/default.png';
};

const data = getCoachData();
const filteredData = ref([...data]);

const positions = ref([
    { label: 'Вратарь', checked: false, type: "goalkeeper" },
    { label: 'Защитник', checked: false, type: "defender" },
    { label: 'Форвард', checked: false, type: "forward" },
    { label: 'Полузащитник', checked: false, type: "midfielder" }
]);

const handleClickSearch = () => {
    const selectedPositions = positions.value.filter(pos => pos.checked).map(pos => pos.label);
    if (selectedPositions.length > 0) {
        filteredData.value = data.filter(item => selectedPositions.includes(item.position));
    } else {
        filteredData.value = [...data];
    }
};
</script>

<template>
    <div class="flex justify-between bg-[#1C1C2E] p-7 rounded-3xl">
        <div class="px-4 flex justify-between w-full">
            <!-- Используем индекс для генерации уникального id -->
            <div v-for="(pos, index) in positions" :key="index" class="flex items-center">
                <input type="checkbox" v-model="pos.checked" :id="`custom-checkbox-${index}`" class="hidden" />
                <label :for="`custom-checkbox-${index}`"
                    class="cursor-pointer relative w-[18px] h-[18px] bg-[#45455E] rounded-[4px] flex items-center justify-center transition duration-500">
                    <span class="absolute inset-0 bg-[#45455E] rounded-[10px] transition duration-500"
                        :class="{ 'bg-[#FEFEFE]': pos.checked }"></span>
                    <img v-if="pos.checked" src="/src/assets/icons/check-mark.svg" alt="Check mark"
                        class="absolute left-[4px] bottom-[-3px] w-7 h-7" />
                </label>
                <span class="block text-[#FEFEFE] ps-4">{{ pos.label }}</span>
            </div>
            <div>
                <button @click="handleClickSearch" class="text-[#FEFEFE] bg-[#0046AD] rounded-3xl px-8 py-3">
                    Поиск
                </button>
            </div>
        </div>
    </div>

    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-4 mt-6">
        <!-- Отображаем данные -->
        <div v-for="item in filteredData" :key="item.id" class="text-[#FEFEFE]">
            <div class="w-full">
                <div class="bg-[#1C1C2E] cursor-pointer rounded-3xl px-7 py-6 w-full flex flex-col gap-2">
                    <div class="flex justify-center w-full max-w-[124px] mx-auto">
                        <img :src="getIcon(item.position)" class="max-w-full h-auto"
                            :alt="`${item.position} ${item.name}`" :data-name="item.position" />
                    </div>
                    <div class="text-[#FEFEFE] font-semibold">{{ item.name }}</div>
                    <div class="text-[#B4B4C4]">Позиция: <br> {{ item.position }}</div>
                    <div class="text-[#B4B4C4]">Возраст: {{ item.age }}</div>
                </div>
            </div>
        </div>
    </div>
</template>