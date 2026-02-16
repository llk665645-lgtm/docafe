<template>
  <NuxtLayout>
    <AppHeader />
    <TextCursor
      :delay="0.01"
      :spacing="80"
      :follow-mouse-direction="true"
      :random-float="true"
      :exit-duration="0.5"
      :max-points="10"
    />

    <Analytics/>
    <NuxtPage />
  </NuxtLayout>
</template>

<script setup lang="ts">
import { Analytics } from '@vercel/analytics/nuxt'

useHead({
  link: [
    { rel: 'icon', type: 'image/svg+xml', href: '/logo.svg' }
  ]
})
</script>