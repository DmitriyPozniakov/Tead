<script setup lang="ts">
import { onMounted, ref, onBeforeUnmount } from 'vue'

const deals = [
    { title: 'NEAR/USDT', subTitle: 'SPOT · 1 мин. назад', profit: '58.6206', targetNum: '4', date: '06.10.2022' },
    { title: 'BTC/USDT', subTitle: 'SPOT · 2 мин. назад', profit: '48000', targetNum: '2', date: '06.10.2022' },
    { title: 'ETH/USDT', subTitle: 'SPOT · 3 мин. назад', profit: '3200', targetNum: '3', date: '06.10.2022' },
    { title: 'XRP/USDT', subTitle: 'SPOT · 4 мин. назад', profit: '1.05', targetNum: '5', date: '06.10.2022' },
    { title: 'ADA/USDT', subTitle: 'SPOT · 5 мин. назад', profit: '2.15', targetNum: '6', date: '06.10.2022' },
    { title: 'NEAR/USDT', subTitle: 'SPOT · 1 мин. назад', profit: '58.6206', targetNum: '4', date: '06.10.2022' },
    { title: 'BTC/USDT', subTitle: 'SPOT · 2 мин. назад', profit: '48000', targetNum: '2', date: '06.10.2022' },
    { title: 'ETH/USDT', subTitle: 'SPOT · 3 мин. назад', profit: '3200', targetNum: '3', date: '06.10.2022' },
    { title: 'XRP/USDT', subTitle: 'SPOT · 4 мин. назад', profit: '1.05', targetNum: '5', date: '06.10.2022' },
    { title: 'ADA/USDT', subTitle: 'SPOT · 5 мин. назад', profit: '2.15', targetNum: '6', date: '06.10.2022' }
]

const hScroll = ref<HTMLElement | null>(null)
const wrapper = ref<HTMLElement | null>(null)

onMounted(async () => {
    const { gsap } = await import('gsap')
    const { ScrollTrigger } = await import('gsap/ScrollTrigger')
    
    gsap.registerPlugin(ScrollTrigger)

    const el = hScroll.value
    const wrap = wrapper.value
    if (!el || !wrap) return

    ScrollTrigger.matchMedia({
        "(min-width: 320px)": function () {
            const totalWidth = el.scrollWidth
            const scrollDistance = totalWidth - window.innerWidth

            gsap.to(el, {
                x: -scrollDistance,
                ease: "none",
                scrollTrigger: {
                    trigger: wrap,
                    start: "top top",
                    end: "+=" + scrollDistance * 2,
                    scrub: 0.5,
                    pin: true,
                    anticipatePin: 1,
                }
            })
        }
    })
})

onBeforeUnmount(async () => {
    const { ScrollTrigger } = await import('gsap/ScrollTrigger')
    ScrollTrigger.getAll().forEach(trigger => trigger.kill())
})
</script>

<template>
    <section ref="wrapper" class="pt-40 pb-60 bg-[#030718] overflow-hidden relative">
        <h2 class="text-3xl md:text-5xl font-bold uppercase text-white tracking-[-2px] mb-4">
            Прошедшие сделки
        </h2>

        <div class="flex items-center gap-2 mb-10">
            <div class="w-[8px] h-[8px] rounded-full bg-[#35FF9E]"></div>
            <p class="text-[#35FF9E] text-sm">Онлайн</p>
        </div>

        <div ref="hScroll" class="flex items-center gap-6 will-change-transform">
            <BaseCard v-for="(deal, index) in deals" :key="index" v-bind="deal" />
        </div>

        <img class="absolute -bottom-2 left-0 hidden md:block" src="~/assets/icons/whiteSeparator.svg" alt="">
        <img class="absolute -bottom-10 left-0 block md:hidden" src="~/assets/icons/whiteSeparatorMob.svg" alt="">
    </section>
</template>