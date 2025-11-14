<script setup lang="ts">
defineProps<{
  text: string
  border?: boolean
  rounded?: string
  bg?: string
  color?: string
  shadow?: boolean
  px?: string
  py?: string
}>()
</script>

<template>
  <button
    class="cursor-pointer uppercase font-medium flex flex-col transition-transform transition-colors duration-200 ease-in-out hover:scale-105 hover:brightness-110"
    :class="[rounded, bg, color, px, py]"
    :style="{
      boxShadow: shadow ? '0px 0px 4px 0px #57E1FF' : '',
      border: border ? '1.5px solid #57E1FF' : ''
    }"
  >
    {{ text }}
    <slot></slot>
  </button>
</template>
