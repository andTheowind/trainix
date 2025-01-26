<script setup>
import { ref, onMounted } from 'vue'

const isDropdownVisible = ref(false)
const userName = ref('')

const updateUserName = () => {
  const storedUserInfo = localStorage.getItem('userInfo')
  if (storedUserInfo) {
    const { name, surname } = JSON.parse(storedUserInfo)
    userName.value = `${surname} ${name}`
  }
}

window.addEventListener('storage_userInfo', () => {
  updateUserName()
})

onMounted(() => {
  updateUserName()
})

const toggleDropdown = () => {
  isDropdownVisible.value = !isDropdownVisible.value;
}

defineEmits(['update:modelValue']);
</script>

<template>
  <header class="bg-[#1E1E2D] h-20 w-full">
    <div class="w-full max-w-[1440px] mx-auto px-5 h-full flex justify-between items-center">
      <div class="flex items-center gap-[60px]">
        <div class="w-[140px] h-10 flex items-center">
          <a href="./"><span class="text-[#8D8BA2]">Найди тренера</span></a>
        </div>
      </div>
      <div class="relative" @click="toggleDropdown">
        <div>
          <!-- User Profile Image -->
        </div>
        <div class="flex items-center gap-2 cursor-pointer">
          <span class="text-white">{{ userName }}</span>
          <img src="/src/assets/icons/arrow-down.svg" alt="Dropdown" class="w-4 h-4 transition-transform duration-200"
            :class="{ 'rotate-180': isDropdownVisible }">
        </div>
        <div v-if="isDropdownVisible"
          class="absolute right-0 top-full mt-2 bg-[#1E1E2D] rounded-lg shadow-lg py-2 min-w-[160px]">
          <ul class="list-none p-0 m-0">
            <li class="hover:bg-gray-700">
              <a @click="$emit('update:modelValue', 'Мои настройки')" href="#"
                class="block px-4 py-2 text-[#92929F] hover:text-white transition-colors">
                Настройки
              </a>
            </li>
            <li class="hover:bg-gray-700">
              <a @click="$emit('update:modelValue', 'Поддержка')" href="#"
                class="block px-4 py-2 text-[#92929F] hover:text-white transition-colors">
                Поддержка
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </header>
</template>