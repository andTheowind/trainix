<script>
import SideBar from '@/components/sidebar/SideBar.vue';
import MainContent from '@/components/main-content/tabs/MainContent.vue';
import UserNameModal from '@/components/main-content/UserNameModal.vue';

export default {
    components: {
        SideBar,
        MainContent,
        UserNameModal
    },
    props: {
        currentWindow: {
            type: String,
            required: true
        }
    },
}
</script>

<template>
    <div class="bg-[#131420] flex min-h-[calc(100vh-168px)] w-full mx-auto">
        <div class="max-w-[1440px] flex mx-auto w-full px-5 py-4 gap-6">
            <SideBar @updateWindow="$emit('updateWindow', $event)" :currentWindow="currentWindow" />
            <MainContent :currentWindow="currentWindow" />
        </div>
    </div>

    <UserNameModal />
</template>