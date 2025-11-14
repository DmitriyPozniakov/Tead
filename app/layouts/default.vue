<script setup lang="ts">
import TheNavigation from '~/components/TheNavigation.vue'
import TheFooter from '~/components/TheFooter.vue'
</script>

<template>
  <div class="flex flex-col min-h-screen max-w-[1440px] w-full mx-auto">
    <TheNavigation />

    <main class="flex-1">
      <NuxtPage />
    </main>

    <TheFooter />
  </div>
</template>
