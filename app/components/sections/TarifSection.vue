<script setup lang="ts">
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs'

const tarifs = [
  {
    titleTab: 'СПОТ',
    value: 'standart',
    cards: [
      {
        title: 'Standart',
        included: [
          'Ручной трейдинг',
          'Автоматическое или полуавтоматическое копирование сделок',
          'Личный кабинет со статистикой',
          'Среднесрочные сделки с уровнями набора портфеля'
        ],
        price: '234',
        discount: '35',
        bg: 'bg-transparent',
        border: true,
        borderColor: 'black'
      },
      {
        title: 'vip',
        included: [
          'Ручной трейдинг',
          'Автоматическое или полуавтоматическое копирование сделок',
          'Личный кабинет со статистикой',
          'Краткосрочные, среднесрочные и инвест сделки',
          'Доступ в Vip чат с командой',
          'Наш авторский курс по трейдингу',

        ],
        price: '450',
        discount: '20',
        bg: 'bg-[#6A54FF]',
        border: false,
        borderColor: 'white'
      }
    ]
  },
  {
    titleTab: 'ФЬЮЧЕРС',
    value: 'vip',
    cards: [
      {
        title: 'Futures PRO',
        included: [
          'Ручной трейдинг на фьючерсах',
          'Автоматическое копирование сделок',
          'Личный кабинет со статистикой PnL',
          'Отдельные сигналы по фьючерсам BTC/ETH/alt',
          'Рекомендации по плечам и риск-менеджменту',
          'Ежедневные разборы рынка'
        ],
        price: '320',
        discount: '25',
        bg: 'bg-transparent',
        border: true,
        borderColor: 'black'
      },
      {
        title: 'Futures ELITE',
        included: [
          'Полный доступ к фьючерсным сигналам',
          'Алгоритмическое копирование сделок с управлением рисками',
          'Личный кабинет со всеми метриками (PnL, Max Drawdown)',
          'Vip чат с командой трейдеров',
          'Эксклюзивные сделки на сильных движениях',
          'Zoom-разборы 2 раза в неделю',
          'Авторские уроки по фьючерсам'
        ],
        price: '690',
        discount: '30',
        bg: 'bg-[#6A54FF]',
        border: false,
        borderColor: 'white'
      }
    ]
  }
]
</script>

<template>
  <section class="py-20 bg-[#030718]" data-aos="fade-up">
    <div class="flex flex-col w-full max-w-[800px] mx-auto">

      <h2 class="uppercase font-bold text-3xl md:text-5xl text-white mb-8 text-center md:text-left">
        Тарифы
      </h2>

      <Tabs default-value="standart" class="w-full flex flex-col items-start">

        <TabsList class="mb-4 flex justify-center md:justify-start mb-10">
          <TabsTrigger
            v-for="tarif in tarifs"
            :key="tarif.value"
            :value="tarif.value"
            class="uppercase"
          >
            {{ tarif.titleTab }}
          </TabsTrigger>
        </TabsList>

        <TabsContent
          v-for="tarif in tarifs"
          :key="tarif.value"
          :value="tarif.value"
          class="w-full"
        >
          <div class="flex flex-col md:flex-row items-center justify-start md:items-stretch gap-6">
            <BaseTariff
              v-for="card in tarif.cards"
              :key="card.title"
              :title="card.title"
              :included="card.included"
              :price="card.price"
              :discount="card.discount"
              :bg="card.bg"
              :border="card.border"
              :border-color="card.borderColor"
            />
          </div>
        </TabsContent>

      </Tabs>
    </div>
  </section>
</template>

