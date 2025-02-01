<script>
import IconSet from '@/components/icons/IconsSet.vue';

export default {
    data() {
        return {
            navigations: [{
                icon: "home",
                text: "Главная"
            }, {
                icon: "profile",
                text: "Профиль"
            }, {
                icon: "mail",
                text: "Поиск тренера"
            }, {
                icon: "settings",
                text: "Мои настройки"
            }, {
                icon: "help",
                text: "Поддержка"
            }]
        }
    },
    components: {
        IconSet
    },
    props: {
        currentWindow: {
            type: String,
            required: true
        }
    },
    methods: {
        handleClick(page) {
            this.$emit('updateWindow', page);
        }
    },
}
</script>

<template>
    <div class="flex flex-col min-w-fit gap-x-3 gap-y-4 mt-5 text-[#8D8BA2]">
        <a v-for="item in navigations" :key="item.icon" @click="handleClick(item.text)"
            :class="['flex', 'justify-start', 'select-none', 'cursor-pointer', { 'text-[#7AB0FF]': currentWindow === item.text }]">
            <IconSet :name="item.icon" :color="currentWindow === item.text ? '#7AB0FF' : '#8D8BA2'" />
            <span class="block ps-3">{{ item.text }}</span>
        </a>

    </div>
</template>