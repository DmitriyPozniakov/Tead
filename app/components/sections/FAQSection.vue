<script setup lang="ts">
import { Accordion, AccordionContent, AccordionItem, AccordionTrigger } from "@/components/ui/accordion"

const defaultValue = "item-1"

const accordionItems = [
    {
        value: "item-1", title: "Что такое TradeBlade", content: "Мы опытная команда, для которой трейдинг – профессия. TradeBlade является авторизованным официальным брокером биржи Binance. Он представляет пользователям множество преимуществ, таких как более високая скорость синхронизации API и возможность создать учетную запись Binance через платформу TradeBlade всего в 1 клик."
    },
    { value: "item-2", title: "Что TradeBlade предлагает инвесторам", content: "Мы опытная команда, для которой трейдинг – профессия. TradeBlade является авторизованным официальным брокером биржи Binance. Он представляет пользователям множество преимуществ, таких как более високая скорость синхронизации API и возможность создать учетную запись Binance через платформу TradeBlade всего в 1 клик." },
    { value: "item-3", title: "Должен ли я перевести свои средства на TradeBlade", content: "Мы опытная команда, для которой трейдинг – профессия. TradeBlade является авторизованным официальным брокером биржи Binance. Он представляет пользователям множество преимуществ, таких как более високая скорость синхронизации API и возможность создать учетную запись Binance через платформу TradeBlade всего в 1 клик." },
]
</script>

<template>
    <section class="flex flex flex-col items-center justify-center py-20">
        <div class="max-w-[800px] w-full">
            <h2 class="uppercase text-black text-left text-3xl md:text-5xl text-left font-bold mb-6">часто задаваемые вопросы</h2>

            <Accordion type="single" class="w-full" collapsible :default-value="defaultValue">
                <AccordionItem v-for="item in accordionItems" :key="item.value" :value="item.value">
                    <AccordionTrigger class="text-2xl">{{ item.title }}</AccordionTrigger>
                    <AccordionContent class="text-base">
                        {{ item.content }}
                    </AccordionContent>
                </AccordionItem>
            </Accordion>
        </div>

    </section>

</template>