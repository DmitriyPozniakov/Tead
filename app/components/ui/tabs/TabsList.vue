<script setup lang="ts">
import type { TabsListProps } from "reka-ui"
import type { HTMLAttributes } from "vue"
import { reactiveOmit } from "@vueuse/core"
import { TabsList } from "reka-ui"
import { cn } from "@/lib/utils"

const props = defineProps<TabsListProps & { class?: HTMLAttributes["class"] }>()

const delegatedProps = reactiveOmit(props, "class")
</script>

<template>
  <TabsList
    data-slot="tabs-list"
    v-bind="delegatedProps"
    :class="cn( 
      'bg-[#2C2674] text-muted-foreground inline-flex h-12 gap-2 w-full md:max-w-[410px] items-center justify-center rounded-[4px] p-[3px]',
      props.class,
    )"
  >
    <slot />
  </TabsList>
</template>
