<script setup>
const cardItems = [
    {id: 1, title: 'Опытные профессионалы'},
    {id: 2, title: 'Квалифицированные тренеры'},
    {id: 3, title: 'Специализированне мастера'},
]
</script>

<template>
    <div  class="flex justify-center gap-6 pt-5 pb-4">
        <div v-for="card in cardItems" :key="card.id" class="flex items-center gap-4">
            <div>
                <img src="/src/assets/icons/Ellipse.svg" class="max-w-full h-auto">
            </div>
            <p class="text-[#FEFEFE] pb-1"> {{ card.title }} </p>
        </div>
    </div>
</template>
