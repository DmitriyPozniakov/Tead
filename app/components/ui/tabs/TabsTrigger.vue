<script setup lang="ts">
import type { TabsTriggerProps } from "reka-ui"
import type { HTMLAttributes } from "vue"
import { reactiveOmit } from "@vueuse/core"
import { TabsTrigger, useForwardProps } from "reka-ui"
import { cn } from "@/lib/utils"

const props = defineProps<TabsTriggerProps & { class?: HTMLAttributes["class"] }>()

const delegatedProps = reactiveOmit(props, "class")

const forwardedProps = useForwardProps(delegatedProps)
</script>

<template>
  <TabsTrigger data-slot="tabs-trigger" v-bind="forwardedProps" :class="cn(
    `
      inline-flex flex-1 items-center justify-center
      rounded-[4px] border border-transparent
      whitespace-nowrap transition-all
      text-[24px] uppercase

      text-[#57E1FF]      

      p-4

      font-medium
      data-[state=active]:font-bold
      data-[state=active]:text-black
      data-[state=active]:bg-[#57E1FF]
      data-[state=active]:p-4
      data-[state=active]: w-full

      h-[calc(100%-1px)]
      focus-visible:ring-[3px]
      focus-visible:outline-1
      disabled:pointer-events-none disabled:opacity-50
      [&_svg]:pointer-events-none [&_svg]:shrink-0 [&_svg:not([class*='size-'])]:size-4
    `,
    props.class
  )
    ">
    <slot />
  </TabsTrigger>
</template>
