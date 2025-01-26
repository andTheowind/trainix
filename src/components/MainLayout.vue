<script setup>
import SideBar from '@/components/sidebar/SideBar.vue';
import MainContent from '@/components/main-content/tabs/MainContent.vue';
import UserNameModal from '@/components/main-content/UserNameModal.vue'

defineEmits(['update:modelValue']);
const props = defineProps({
    currentWindow: {
        type: String,
        required: true,
    },
});

console.log(props.currentWindow);
</script>

<template>
    <div class="bg-[#131420] flex min-h-[calc(100vh-168px)] w-full mx-auto">
        <div class="max-w-[1440px] flex mx-auto w-full px-5 py-4 gap-6">
            <SideBar @update:modelValue="$emit('update:modelValue', $event)" :currentWindow="currentWindow" />
            <MainContent :currentWindow="currentWindow" />
        </div>
    </div>

    <UserNameModal />
</template>