<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const numbers = [
  {
    text: 'торговой прибыли',
    number: '2756%'
  },
  {
    text: 'фьючерсных и спотовых сделок',
    number: '67'
  },
  {
    text: 'прибыль подписчиков',
    number: '375000'
  },
]

const sectionRef = ref<HTMLElement | null>(null)
const animatedNumbers = ref(numbers.map(() => '0'))
const hasAnimated = ref(false)

const animateNumber = (target: string, index: number) => {
  const numericValue = parseInt(target.replace(/\D/g, ''))
  const suffix = target.replace(/[\d]/g, '')
  const duration = 1000
  const steps = 60
  const increment = numericValue / steps
  let current = 0
  let step = 0

  const timer = setInterval(() => {
    step++
    current += increment
    
    if (step >= steps) {
      animatedNumbers.value[index] = target
      clearInterval(timer)
    } else {
      animatedNumbers.value[index] = Math.floor(current) + suffix
    }
  }, duration / steps)
}

const handleIntersection = (entries: IntersectionObserverEntry[]) => {
  entries.forEach(entry => {
    if (entry.isIntersecting && !hasAnimated.value) {
      hasAnimated.value = true
      numbers.forEach((item, index) => {
        animateNumber(item.number, index)
      })
    }
  })
}

let observer: IntersectionObserver | null = null

onMounted(() => {
  if (sectionRef.value) {
    observer = new IntersectionObserver(handleIntersection, {
      threshold: 0.8
    })
    observer.observe(sectionRef.value)
  }
})

onUnmounted(() => {
  if (observer && sectionRef.value) {
    observer.unobserve(sectionRef.value)
  }
})
</script>

<template>
  <section ref="sectionRef" class="flex flex-col lg:flex-row justify-between w-full py-20">
    <div class="flex flex-col mb-8 md:mb-0">
      <p class="font-bold text-[44px] tracking-[-2px] uppercase leading-none">Цифры</p>
      <p class="text-sm text-[#A0A0A0] mt-1">Сентябрь 2022</p>
    </div>

    <div
      class="grid grid-cols-2 gap-x-8 gap-y-6 lg:flex lg:justify-between lg:gap-16 w-full lg:w-auto lg:flex-1 lg:ml-20 items-stretch">
      <div v-for="(item, index) in numbers" :key="index" class="flex flex-col justify-between h-full">
        <p class="uppercase leading-[20px] text-sm mb-1 md:max-w-none" :class="index === 0 ? 'max-w-[107px]' : ''">
          {{ item.text }}
        </p>
        <p class="font-medium tracking-[-2px] text-[#6A54FF] text-4xl lg:text-6xl">
          {{ animatedNumbers[index] }}
        </p>
      </div>
    </div>
  </section>
</template>