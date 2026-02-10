<template>
  <div class="bg-brand-light min-h-screen">
    <HeroSection />
    <FeaturesSection />
    <StepsSection />

    <section class="py-24 bg-white">
      <div class="mx-auto max-w-7xl px-6 lg:px-8">
        <div class="bg-background relative h-[500px] w-full overflow-hidden rounded-lg border">
          <div class="mt-[64px] flex justify-center px-12">
            <TestimonialSlider :testimonials="testimonials" />
          </div>
        </div>
      </div>
    </section>

    <CTASection />
    <AppFooter />
  </div>
</template>

<script setup lang="ts">
import { rand } from "@vueuse/core"
import HeroSection from '~/components/HeroSection.vue'
import FeaturesSection from '~/components/FeaturesSection.vue'
import StepsSection from '~/components/StepsSection.vue'

import CTASection from '~/components/CTASection.vue'
import AppFooter from '~/components/AppFooter.vue'

function getRandomNumber() {
  return rand(1, 99);
}

const testimonials = [
  {
    img: `https://randomuser.me/api/portraits/men/${getRandomNumber()}.jpg`,
    quote:
      "Inspira UI is sleeker than my star cruiser. Launch-ready in seconds. Zero crashes, zero gravity.",
    name: "Buzz Lightyear",
    role: "Intergalactic Interface Command",
  },
  {
    img: `https://randomuser.me/api/portraits/women/${getRandomNumber()}.jpg`,
    quote:
      "Clickin' around this thing feels like ridin' a horse with turbo boosters. Inspira’s got giddyup!",
    name: "Jessie",
    role: "Yeehaw Engagement & Barnyard UX",
  },
  {
    img: `https://randomuser.me/api/portraits/men/${getRandomNumber()}.jpg`,
    quote:
      "I’ve seen some clunky UIs in my day... but this one? Smoother than a tumbleweed on Tuesday.",
    name: "Woody",
    role: "Sheriff",
  },
  {
    img: `https://randomuser.me/api/portraits/men/${getRandomNumber()}.jpg`,
    quote:
      "I was terrified. Then I clicked. Nothing exploded. Inspira UI is a safe space. I’m thriving.",
    name: "Rex",
    role: "Senior Panic Tester, Dinosaur Usability Lab",
  },
]

useHead({
  title: 'Secure Document Sharing & Control',
  meta: [
    { name: 'description', content: 'Securely share, track, and manage your sensitive documents. Revoke access instantly and get detailed analytics.' }
  ]
})
</script>


