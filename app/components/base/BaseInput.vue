<script setup lang="ts">
defineProps<{
    placeholder: string
    bg: string,
    color: string
}>()

</script>

<template>
    <div class="relative w-full max-w-[500px]">
        <input type="email" :placeholder="placeholder"
            :class="[bg, color]" class="w-full placeholder-[#6B5BA8] px-6 py-4 pr-[140px] rounded-[3px] border border-[#4A3B8C] focus:outline-none focus:border-[#57E1FF] transition-colors uppercase" />
        <div class="absolute right-2 top-1/2 -translate-y-1/2">
            <BaseButton text="начать" bg="bg-[#57E1FF]" rounded="rounded-[3px]" :border="true" color="text-[#030718]"
                :shadow="true" px="px-6" py="py-[11px]" />
        </div>
    </div>
</template>