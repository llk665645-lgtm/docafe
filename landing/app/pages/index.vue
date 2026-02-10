<template>
  <div class="bg-brand-light min-h-screen">
    <HeroSection />
    <FeaturesSection />
    <StepsSection />
    <DesignTestimonials :testimonials="testimonials" />

    <CTASection />
    <AppFooter />
  </div>
</template>

<script setup lang="ts">
import HeroSection from '~/components/HeroSection.vue'
import FeaturesSection from '~/components/FeaturesSection.vue'
import StepsSection from '~/components/StepsSection.vue'
import DesignTestimonials from '~/components/DesignTestimonials.vue'

import CTASection from '~/components/CTASection.vue'
import AppFooter from '~/components/AppFooter.vue'

const testimonials = [
  {
    quote:
      "The component structure is clear, flexible, and surprisingly elegant. It just works—no shadow clones required.",
    author: "Naruto Uzumaki",
    role: "Lead Frontend Ninja",
    company: "Hidden Leaf Labs",
  },
  {
    quote:
      "Thoughtful motion, precise timing, and no unnecessary noise. Design should feel effortless—this does.",
    author: "Itachi Uchiha",
    role: "Architect of Interfaces",
    company: "Akatsuki Systems",
  },
  {
    quote: "Clean visuals, smooth transitions, and zero friction. Honestly? It feels limitless.",
    author: "Gojo Satoru",
    role: "UI Performance Engineer",
    company: "Jujutsu Tech",
  },
  {
    quote:
      "Every detail feels intentional. The balance between motion and restraint is… impressive.",
    author: "Jin Sunwoo",
    role: "Product Strategist",
    company: "Shadow Guild",
  },
]

useHead({
  title: 'Secure Document Sharing & Control',
  meta: [
    { name: 'description', content: 'Securely share, track, and manage your sensitive documents. Revoke access instantly and get detailed analytics.' }
  ]
})
</script>
