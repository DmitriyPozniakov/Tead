<script setup lang="ts">
const props = defineProps<{
    bg: string
    border: boolean
    borderColor?: string
    title: string
    included: string[]
    price: string
    discount: string
}>()

const liBorderColor = props.borderColor === 'white' ? '#8876FF' : '#353946'
</script>

<template>
    <div :class="[bg]" class="py-4 bg-[#1a1a2e] rounded-lg max-w-[410px] w-full flex flex-col"
        :style="border ? 'border: 1px solid #6A54FF' : ''">
        <h3
            class="px-4 text-xl font-bold text-white mb-4 uppercase text-xl md:text-3xl w-full max-w-[440px] min-w-[340px] mb-4 md:mb-15">
            {{ props.title }}
        </h3>

        <ul class="text-white/80 flex-1">
            <li class="border-b border-dashed px-4 py-2 flex items-start gap-2 text-white text-base"
                v-for="item in props.included" :key="item" :style="`border-color: ${liBorderColor}`">
                <img src="~/assets/icons/check.svg" alt="" class="translate-y-[7px]" />
                <span>{{ item }}</span>
            </li>
        </ul>

        <div class="p-4 mt-8 relative w-fit flex items-start">
            <p class="text-white font-medium text-4xl">${{ props.price }}</p>
            <span class="absolute top-0 -right-7 text-[#35FF9E] font-medium text-lg">
                -{{ props.discount }}%
            </span>
        </div>

        <div class="px-4">
            <BaseButton text="Попробовать" bg="bg-[#57E1FF]" rounded="rounded-[3px]" :border="true"
                color="text-[#030718]" :shadow="true" px="px-6" py="py-[4px]" class="w-full "><span
                    class="text-xs opacity-40">5 дней бесплатно</span></BaseButton>
        </div>
    </div>
</template>
