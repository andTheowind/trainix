<script>
export default {
    data() {
        return {
            socialItems: [
                { id: 1, icon: '/src/assets/icons/in-icon.svg', link: 'https://linkedin.com' },
                { id: 2, icon: '/src/assets/icons/vk-icon.svg', link: 'https://vk.com' }
            ]
        }
    }
}
</script>

<template>
    <ul class="flex items-center gap-3">
        <li v-for="item in socialItems" :key="item.id" class="flex items-center">
            <a :href="`${item.link}`" target="_blank">
                <img :src="item.icon" class="w-full h-auto" alt="">
            </a>
        </li>
    </ul>
</template>