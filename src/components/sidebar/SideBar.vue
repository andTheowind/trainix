<script setup>
import IconSet from '@/components/icons/IconsSet.vue';
import { ref, watch } from 'vue';

const emit = defineEmits(['update:modelValue']);

const props = defineProps({
    currentWindow: {
        type: String,
        required: true
    }
});

const handleClick = (page) => {
    emit('update:modelValue', page);
}

const currentWindow = ref(props.currentWindow)
watch(() => props.currentWindow, (newValue) => {
    currentWindow.value = newValue;
})
console.log(currentWindow);
</script>

<template>
    <div class="flex flex-col min-w-fit gap-x-3 gap-y-4 mt-5 text-[#8D8BA2]">
        <a @click="handleClick('Главная')"
            :class="['flex', 'justify-start', 'select-none', 'cursor-pointer', { 'text-[#7AB0FF]': currentWindow === 'Главная' }]">
            <IconSet name="home" :color="currentWindow === 'Главная' ? '#7AB0FF' : '#8D8BA2'" />
            <span class="block ps-3">Главная</span>
        </a>
        <a @click="handleClick('Профиль')"
            :class="['flex', 'justify-start', 'select-none', 'cursor-pointer', { 'text-[#7AB0FF]': currentWindow === 'Профиль' }]">
            <IconSet name="profile" :color="currentWindow === 'Профиль' ? '#7AB0FF' : '#8D8BA2'" />
            <span class="block ps-3">Профиль</span>
        </a>
        <a @click="handleClick('Поиск тренера')"
            :class="['flex', 'justify-start', 'select-none', 'cursor-pointer', { 'text-[#7AB0FF]': currentWindow === 'Поиск тренера' }]">
            <IconSet name="mail" :color="currentWindow === 'Поиск тренера' ? '#7AB0FF' : '#8D8BA2'" />
            <span class="block ps-3">Поиск тренера</span>
        </a>
        <a @click="handleClick('Мои настройки')"
            :class="['flex', 'justify-start', 'select-none', 'cursor-pointer', { 'text-[#7AB0FF]': currentWindow === 'Мои настройки' }]">
            <IconSet name="settings" :color="currentWindow === 'Мои настройки' ? '#7AB0FF' : '#8D8BA2'" />
            <span class="block ps-3">Мои настройки</span>
        </a>
        <a @click="handleClick('Поддержка')"
            :class="['flex', 'justify-start', 'select-none', 'cursor-pointer', { 'text-[#7AB0FF]': currentWindow === 'Поддержка' }]">
            <IconSet name="help" :color="currentWindow === 'Поддержка' ? '#7AB0FF' : '#8D8BA2'" />
            <span class="block ps-3">Поддержка</span>
        </a>
    </div>
</template>