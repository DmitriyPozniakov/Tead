<script setup lang="ts">
import heroImage from "~/assets/images/heroImage.png";
</script>

<template>
  <section
    class="grid blue-bg py-10 lg:py-40 gap-10 md:gap-20 lg:gap-[150px] w-full justify-between md:grid-cols-2 relative pb-20"
  >
    <img :src="heroImage" alt="" class="order-1 md:order-2" data-aos="fade-left" />

    <div data-aos="fade-right" class="order-2 md:order-1 flex flex-1 flex-col gap-3">
      <h1 
        class="uppercase text-4xl tracking-[-4px] leading-[44px] md:leading-[72px] font-bold lg:text-6xl text-white w-full max-w-[630px]"
      >
        моментально <br />
        Копируй сделки <br />
        профи трейдеров
      </h1>
      <p class="my-3 text-[#b9c7cb] leading-[20px] w-full max-w-[565px]">
        Начни копировать сделки с успешной командой профессиональных трейдеров
        в автоматическом режиме.
      </p>
      <BaseInput placeholder="Ваш e–mail" bg="bg-[#2A1F5C]" color="text-white" />
      <p class="text-[#4f515d] text-sm leading-[20px]">5 дней бесплатного пользования</p>
    </div>
    <img class="absolute -bottom-2 left-0 hidden md:block" src="~/assets/icons/whiteSeparator.svg" alt="">
    <img class="absolute -bottom-10 left-0 block md:hidden" src="~/assets/icons/whiteSeparatorMob.svg" alt="">
  </section>
</template>