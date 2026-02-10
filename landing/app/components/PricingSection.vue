<template>
  <section id="pricing" class="bg-brand-light py-24 sm:py-32">
    <div class="mx-auto max-w-7xl px-6 lg:px-8">
      <div class="mx-auto max-w-4xl text-center">
        <h2 class="text-base font-semibold leading-7 text-[#ba445b]">Pricing</h2>
        <p class="mt-2 text-4xl font-bold tracking-tight text-brand-dark sm:text-5xl">
          Choose the right plan for your security needs
        </p>
      </div>
      <p class="mx-auto mt-6 max-w-2xl text-center text-lg leading-8 text-brand-gray">
        Simple, transparent pricing that grows with you. All plans include our core document tracking and revocation technology.
      </p>

      <div class="isolate mx-auto mt-16 grid max-w-md grid-cols-1 gap-y-8 sm:mt-20 lg:mx-0 lg:max-w-none lg:grid-cols-3 lg:gap-x-8 xl:gap-x-12">
        <div v-for="tier in tiers" :key="tier.id" 
             class="relative flex flex-col justify-between rounded-3xl bg-white p-8 ring-1 ring-border sm:p-10 transition-all duration-300 hover:shadow-xl"
             :class="{ 'ring-2 ring-[#ba445b] scale-105 z-10': tier.mostPopular }">
          <div v-if="tier.mostPopular" class="absolute -top-4 left-1/2 -translate-x-1/2 rounded-full bg-[#ba445b] px-4 py-1 text-xs font-bold text-white uppercase tracking-wider">
            Most Popular
          </div>
          <div>
            <h3 :id="tier.id" class="text-base font-semibold leading-7" :class="tier.mostPopular ? 'text-[#ba445b]' : 'text-brand-dark'">
              {{ tier.name }}
            </h3>
            <div class="mt-4 flex items-baseline gap-x-2">
              <span class="text-4xl font-bold tracking-tight text-brand-dark">{{ tier.price }}</span>
              <span v-if="tier.price !== 'Custom'" class="text-sm font-semibold leading-6 text-brand-gray">/month</span>
            </div>
            <p class="mt-6 text-base leading-7 text-brand-gray">
              {{ tier.description }}
            </p>
            <ul role="list" class="mt-10 space-y-4 text-sm leading-6 text-brand-gray">
              <li v-for="feature in tier.features" :key="feature" class="flex gap-x-3">
                <Icon name="lucide:check" class="h-6 w-5 flex-none text-[#ba445b]" aria-hidden="true" />
                {{ feature }}
              </li>
            </ul>
          </div>
          <button
            :aria-describedby="tier.id"
            class="mt-8 block rounded-full px-6 py-3 text-center text-sm font-semibold leading-6 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 transition-all duration-200"
            :class="tier.mostPopular 
              ? 'bg-[#ba445b] text-white shadow-md hover:bg-[#ba445b]/90 hover:scale-105 active:scale-95' 
              : 'bg-brand-light text-brand-dark ring-1 ring-inset ring-border hover:ring-[#ba445b] hover:text-[#ba445b]'"
          >
            {{ tier.cta }}
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const tiers = [
  {
    name: 'Individual',
    id: 'tier-individual',
    price: '$0',
    description: 'Perfect for sharing safe documents with friends and family.',
    features: [
      'Up to 5 active documents',
      'Basic tracking analytics',
      'Instant revocation',
      'Watermarking',
      '48-hour activity log',
    ],
    cta: 'Get started for free',
    mostPopular: false,
  },
  {
    name: 'Professional',
    id: 'tier-professional',
    price: '$19',
    description: 'Designed for independent creators and small businesses.',
    features: [
      'Unlimited active documents',
      'Advanced document analytics',
      'Password protection',
      'Custom expiration dates',
      'Full activity history',
      'Disable downloads/printing',
    ],
    cta: 'Start Pro trial',
    mostPopular: true,
  },
  {
    name: 'Enterprise',
    id: 'tier-enterprise',
    price: 'Custom',
    description: 'Bespoke solutions for large organizations and high-stakes data.',
    features: [
      'SSO & Team management',
      'Custom branding setup',
      'API access for automation',
      'Dedicated support',
      'Audit log exports',
      'On-premise deployment options',
    ],
    cta: 'Contact sales',
    mostPopular: false,
  },
];
</script>
