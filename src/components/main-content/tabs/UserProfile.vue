<script>
export default {
    data() {
        return {
            firstName: localStorage.getItem('name'),
            lastName: localStorage.getItem('surname')
        }
    },
    methods: {
        changeUserName(data) {
            const newFirstName = data.target[0].value;
            const newLastName = data.target[1].value;

            localStorage.setItem('userInfo', JSON.stringify(
                {
                    name: newFirstName,
                    surname: newLastName
                }
            ))
            this.firstName = newFirstName;
            this.lastName = newLastName;
            window.dispatchEvent(new Event('storage_userInfo'));
        }
    }
}
</script>

<template>
    <div class="flex flex-col bg-[#1C1C2E] rounded-3xl py-8 px-12 mt-4">
        <div class="flex items-center gap-4 mb-4">
            <img src="@/assets/icons/profile-icon.svg" alt="Support Icon" class="w-6 h-6">
            <h2 class="text-[#FEFEFE] text-xl font-semibold">Редактирование профиля</h2>
        </div>
        <hr class="border-[#3A3A4A] my-4">
        <div>
            <div class="flex items-center gap-4 py-3 rounded-lg transition-all duration-200">
                <form action="" @submit.prevent="changeUserName">
                    <div class="flex items-center gap-5">
                        <input type="text" name="name" placeholder="Имя"
                            class="bg-[#131420] border border-[#92929F] cursor-pointer rounded-lg ps-3 pe-2 py-2 text-white"
                            v-model="firstName" required>
                        <input type="text" name="surname" placeholder="Фамилия"
                            class="bg-[#131420] border border-[#92929F] cursor-pointer rounded-lg ps-3 pe-2 py-2 text-white"
                            v-model="lastName" required>
                        <button type="submit"
                            class="text-[#FEFEFE] bg-[#0046AD] rounded-3xl px-8 py-3">Изменить</button>
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>