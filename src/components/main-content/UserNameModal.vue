<script>
export default {
    data() {
        return {
            isModalVisible: false,
            name: '',
            surname: ''
        }
    },
    methods: {
        handleSubmit() {
            if (this.name && this.surname) {
                const userInfo = { name: this.name, surname: this.surname };
                localStorage.setItem('userInfo', JSON.stringify(userInfo));
                this.isModalVisible = false;
                window.dispatchEvent(new Event('storage_userInfo'));
            } else {
                alert('Введите имя и фамилию');
            }
        }
    },
    beforeMount() {
        const storedUserInfo = localStorage.getItem('userInfo');
        if (storedUserInfo) {
            const { name: storedName, surname: storedSurname } = JSON.parse(storedUserInfo);
            this.name = storedName;
            this.surname = storedSurname;
        } else {
            this.isModalVisible = true;
        }
    }
}
</script>

<template>
    <div v-if="isModalVisible" class="fixed inset-0 flex items-center justify-center bg-[#131420]/80">
        <div class="flex flex-col items-center bg-[#1C1C2E] rounded-3xl py-8 px-12 text-center">
            <p class="text-[#B4B4C4] text-lg">Как вас зовут?</p>
            <form @submit.prevent="handleSubmit"
                class="flex flex-col gap-4 mt-4 text-[#FEFEFE] text-lg font-semibold w-full">
                <input type="text" placeholder="Имя" v-model="name"
                    class="w-full rounded-md px-4 py-2 bg-[#131420] text-[#FEFEFE] focus:outline-none focus:ring-2 focus:ring-[#B4B4C4]">
                <input type="text" placeholder="Фамилия" v-model="surname"
                    class="w-full rounded-md px-4 py-2 bg-[#131420] text-[#FEFEFE] focus:outline-none focus:ring-2 focus:ring-[#B4B4C4]">
                <button type="submit"
                    class="w-full mt-4 py-2 rounded-md bg-[#B4B4C4] text-[#1C1C2E] font-bold hover:bg-[#A4A4B4]">
                    Сохранить
                </button>
            </form>
        </div>
    </div>
</template>
