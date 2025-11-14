<script setup lang="ts">
import { ref } from "vue";
import logo from "~/assets/icons/logo.svg";
import burger from "~/assets/icons/burger.svg";

const isOpen = ref(false);

const links = [
    { text: "Цифры", to: "#" },
    { text: "Сделки онлайн", to: "#" },
    { text: "о компании", to: "#" },
    { text: "как начать", to: "#" },
    { text: "тарифы", to: "#" },
    { text: "отзывы", to: "#" },
    { text: "FAQ", to: "#" },
];
</script>

<template>
  <nav class="text-[#b3b5ba] blue-bg flex items-center justify-between p-3 md:p-6 relative">
    <img :src="logo" alt="Logo"  />

    <ul class="hidden xl:flex items-center justify-center gap-6">
      <li
        v-for="(link, index) in links"
        :key="index"
        class="uppercase p-2 font-medium transition-colors duration-200 hover:text-white hover:scale-105"
      >
        <router-link :to="link.to">{{ link.text }}</router-link>
      </li>
    </ul>

    <div class="hidden xl:flex items-center gap-3">
      <BaseButton 
        text="вход" 
        bg="bg-[#57E1FF33]" 
        rounded="rounded-[3px]" 
        :border="true" 
        color="text-[#57E1FF]"
        :shadow="true" px="px-6" py="py-[11px]"
        class="transition-transform duration-200 hover:scale-105 hover:bg-[#57E1FF55]"
      />
      <BaseButton 
        text="регистрация" 
        bg="bg-[#57E1FF]" 
        rounded="rounded-[3px]" 
        :border="true"
        color="text-[#030718]" 
        :shadow="true" px="px-6" py="py-[11px]"
        class="transition-transform duration-200 hover:scale-105 hover:bg-[#57E1FFCC]"
      />
    </div>

    <!-- Мобильное меню -->
    <button class="block xl:hidden" @click="isOpen = true">
      <img :src="burger" alt="Menu" class="h-6 w-6" />
    </button>

    <transition name="slide-side">
      <div
        v-if="isOpen"
        class="fixed inset-0 bg-[#6A54FF] text-white p-6 flex flex-col z-[999] w-full h-full"
      >
        <button class="self-end text-3xl" @click="isOpen = false">×</button>

        <ul class="flex flex-col gap-8 mt-10 text-lg font-medium">
          <li
            v-for="(link, index) in links"
            :key="index"
            class="uppercase text-2xl opacity-70 transition-opacity duration-200 hover:opacity-100 hover:text-[#57E1FF]"
          >
            <router-link :to="link.to" @click="isOpen = false">
              {{ link.text }}
            </router-link>
          </li>
        </ul>

        <div class="mt-auto flex gap-3">
          <BaseButton 
            text="регистрация" 
            bg="bg-[#57E1FF]" 
            rounded="rounded-[3px]" 
            :border="true"
            color="text-[#030718]" 
            :shadow="true" px="px-6" py="py-[11px]"
            class="w-full transition-transform duration-200 hover:scale-105 hover:bg-[#57E1FFCC]"
          />
          <BaseButton 
            text="вход" 
            bg="bg-[#57E1FF33]" 
            rounded="rounded-[3px]" 
            :border="true"
            color="text-[#57E1FF]" 
            :shadow="true" px="px-6" py="py-[11px]"
            class="w-full transition-transform duration-200 hover:scale-105 hover:bg-[#57E1FF55]"
          />
        </div>
      </div>
    </transition>
  </nav>
</template>

<style scoped>
.slide-side-enter-active,
.slide-side-leave-active {
  transition: transform 0.35s ease, opacity 0.3s ease;
}

.slide-side-enter-from {
  transform: translateX(-100%);
  opacity: 0.4;
}

.slide-side-enter-to {
  transform: translateX(0);
  opacity: 1;
}

.slide-side-leave-from {
  transform: translateX(0);
  opacity: 1;
}

.slide-side-leave-to {
  transform: translateX(-100%);
  opacity: 0;
}
</style>
