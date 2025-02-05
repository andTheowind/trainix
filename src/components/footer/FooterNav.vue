<script>
export default {
    data() {
        return {
            navPages: [
                { id: 1, title: 'Политика конфиденциальности' },
                { id: 2, title: 'Контакты' },
                { id: 3, title: 'Ещё' }
            ]
        }
    }
}
</script>

<template>
    <nav class="flex items-center gap-x-4 text-[#8D8BA2]">
        <a v-for="page in navPages" :key="page.id" href="#" class="block">{{ page.title }}</a>
    </nav>
</template>