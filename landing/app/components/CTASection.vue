<template>
  <div class="bg-primary">
    <div class="px-6 py-24 sm:px-6 sm:py-32 lg:px-8">
      <div class="mx-auto max-w-2xl text-center">
        <div class="flex flex-col items-center justify-center gap-2">
          <h2 class="text-3xl font-bold tracking-tight text-white sm:text-4xl text-center justify-center">
            {{ $t('cta.title') }}
          </h2>
          <h2 class="text-3xl font-bold tracking-tight text-white/90 sm:text-4xl text-center justify-center">
            {{ $t('cta.subtitle') }}
          </h2>
        </div>
        <p class="mx-auto mt-6 max-w-xl text-lg leading-8 text-white/80">
          {{ $t('cta.description') }}
        </p>
        <div class="mt-10 flex items-center justify-center gap-x-6">
          <button class="rounded-2xl bg-white px-8 py-3.5 text-base font-bold text-primary shadow-xl hover:bg-brand-light hover:scale-105 active:scale-95 transition-all duration-200">
            {{ $t('cta.button') }}
          </button>
          <a href="#how-it-works" class="text-sm font-semibold leading-6 text-white border-b border-white/20 hover:border-white transition-colors">
            {{ $t('cta.link') }} <span aria-hidden="true">→</span>
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
// CTA Section
</script>
