<template>
  <section id="pricing" class="bg-brand-light py-24 sm:py-32">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <div class="mx-auto max-w-4xl text-center">
        <h2 class="text-base font-semibold leading-7 text-primary uppercase tracking-widest">{{ $t('pricing.title') }}</h2>
        <p class="mt-2 text-4xl font-bold tracking-tight text-brand-dark sm:text-5xl">
          {{ $t('pricing.subtitle') }}
        </p>
      </div>
      <p class="mx-auto mt-6 max-w-2xl text-center text-lg leading-8 text-brand-gray">
        {{ $t('pricing.description') }}
      </p>

      <div class="isolate mx-auto mt-16 grid max-w-md grid-cols-1 gap-y-8 sm:mt-20 lg:mx-0 lg:max-w-none lg:grid-cols-3 lg:gap-x-8 xl:gap-x-12">
        <div v-for="tier in tierList" :key="tier.name" 
             class="relative flex flex-col justify-between rounded-3xl bg-white p-8 ring-1 ring-border sm:p-10 transition-all duration-300 hover:shadow-xl"
             :class="{ 'ring-2 ring-primary scale-105 z-10': tier.mostPopular }">
          <div v-if="tier.mostPopular" class="absolute -top-4 left-1/2 -translate-x-1/2 rounded-full bg-primary px-4 py-1 text-xs font-bold text-white uppercase tracking-wider">
            {{ $t('pricing.mostPopular') }}
          </div>
          <div>
            <h3 class="text-base font-semibold leading-7" :class="tier.mostPopular ? 'text-primary' : 'text-brand-dark'">
              {{ tier.name }}
            </h3>
            <div class="mt-4 flex items-baseline gap-x-2">
              <span class="text-4xl font-bold tracking-tight text-brand-dark">{{ tier.price }}</span>
              <span v-if="tier.price !== 'Custom'" class="text-sm font-semibold leading-6 text-brand-gray">{{ $t('pricing.perMonth') }}</span>
            </div>
            <p class="mt-6 text-base leading-7 text-brand-gray">
              {{ tier.description }}
            </p>
            <ul role="list" class="mt-10 space-y-4 text-sm leading-6 text-brand-gray">
              <li v-for="feature in tier.features" :key="feature" class="flex gap-x-3">
                <Icon name="lucide:check" class="h-6 w-5 flex-none text-primary" aria-hidden="true" />
                {{ feature }}
              </li>
            </ul>
          </div>
          <button
            class="mt-8 block rounded-xl px-6 py-3 text-center text-sm font-semibold leading-6 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 transition-all duration-200"
            :class="tier.mostPopular 
              ? 'bg-primary text-white shadow-md hover:bg-primary/90 hover:scale-105 active:scale-95' 
              : 'bg-brand-light text-brand-dark ring-1 ring-inset ring-border hover:ring-primary hover:text-primary'"
          >
            {{ tier.cta }}
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import { useI18n } from 'vue-i18n'
const { tm } = useI18n()

interface Tier {
  name: string
  price: string
  description: string
  features: string[]
  cta: string
  mostPopular?: boolean
}

const tierList = computed(() => tm('pricing.tiers') as Tier[])
</script>
