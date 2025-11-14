<script setup lang="ts">
const props = defineProps<{
    title: string
    subTitle: string
    profit: string
    targetNum: string
    date: string
}>()
</script>

<template>
    <div class="bg-custom font-medium w-full p-5 pb-3 relative rounded-sm flex flex-col justify-between">
        <img src="~/assets/icons/cardLogo.svg" class="absolute top-0 right-0" alt="">
        <div>
            <h2 class="text-xl text-white">{{ props.title }}</h2>
            <p class="text-sm text-white opacity-40 font-normal">{{ props.subTitle }}</p>
        </div>
        <div class="flex flex-col gap-2">
            <p class="text-white opacity-70 text-sm uppercase">Прибыль</p>
            <div class="flex items-center gap-2">
                <p class="text-[#35FF9E] text-3xl">{{ props.profit }}</p>
                <img src="~/assets/icons/arrow.svg" alt="">
            </div>
            <div class="flex items-center justify-between">
                <p class="text-sm text-white opacity-70">Цель {{ props.targetNum }}</p>
                <p class="text-sm text-white opacity-40">Дата выхода {{ props.date }}</p>
            </div>
        </div>
    </div>
</template>

<style scoped>
.bg-custom {
    background-image: url('~/assets/images/cardBg.png');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    min-height: 210px;
    min-width: 300px;
}
</style>