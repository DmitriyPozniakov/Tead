<script setup lang="ts">
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
  <footer class="hidden xl:flex p-8 bg-[#030718] flex-col min-h-[560px] md:min-h-[350px]">
    <div class="flex items-start justify-between w-full">
      <p class="uppercase text-white opacity-40">Быстрая навигация</p>
      <img src="~/assets/icons/logo.svg" alt="">
    </div>

    <div class="mt-auto flex items-center justify-between w-full">
      <ul class="mt-auto flex gap-2 text-white">
        <li
          v-for="(link, index) in links"
          :key="index"
          class="text-base uppercase font-medium p-2 opacity-70 transition-transform transition-colors duration-200 hover:text-white hover:scale-105"
        >
          <router-link :to="link.to">{{ link.text }}</router-link>
        </li>
      </ul>
      <p class="text-white opacity-50">© 2022 TradeBlade. All rights reserved</p>
    </div>
  </footer>

  <footer class="flex xl:hidden flex-col p-0 m-0 bg-[#030718]">
    <div class="flex items-start justify-between w-full p-5">
      <p class="uppercase text-white opacity-40">Быстрая навигация</p>
      <ul class="mt-auto flex flex-col gap-3 text-white">
        <li
          v-for="(link, index) in links"
          :key="index"
          class="text-base uppercase font-medium opacity-70 transition-transform transition-colors duration-200 hover:text-white hover:scale-105"
        >
          <router-link :to="link.to">{{ link.text }}</router-link>
        </li>
      </ul>
    </div>
    <div class="bg-gray-500 h-[1px] w-full my-3"></div>
    <div class="mx-6">
      <img src="~/assets/icons/logo.svg" class="mb-15" alt="">
      <p class="mt-auto text-white opacity-50">© 2022 TradeBlade. All rights reserved</p>
    </div>
  </footer>
</template>
