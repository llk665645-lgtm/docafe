<template>
  <div class="flex flex-col items-center justify-center py-12">
    <div class="relative w-48 h-64 overflow-hidden rounded-3xl bg-brand-light/20 border border-brand-light/30">
      <svg viewBox="0 0 200 300" class="w-full h-full drop-shadow-xl" preserveAspectRatio="xMidYMax meet">
        <!-- Pot -->
        <path d="M70,260 L130,260 L140,220 L60,220 Z" fill="#7c2d12" />
        
        <!-- Stem -->
        <path 
          ref="stemRef"
          d="M100,220 Q100,150 100,80" 
          fill="none" 
          stroke="#16a34a" 
          stroke-width="6" 
          stroke-linecap="round"
          class="stem"
        />

        <!-- Leaves -->
        <g ref="leavesRef">
          <path d="M100,180 Q130,170 140,150 Q110,160 100,180" fill="#22c55e" class="leaf opacity-0" />
          <path d="M100,140 Q70,130 60,110 Q90,120 100,140" fill="#22c55e" class="leaf opacity-0" />
        </g>

        <!-- Flower -->
        <g ref="flowerRef" transform="translate(100, 80) scale(0)">
          <!-- Petals -->
          <circle v-for="i in 6" :key="i" cx="0" :cy="-15" r="15" :fill="color" :transform="`rotate(${(i-1)*60})`" />
          <!-- Center -->
          <circle cx="0" cy="0" r="10" fill="#facc15" />
        </g>
      </svg>
    </div>
    <div class="mt-6 text-brand-gray font-serif italic text-lg animate-pulse">
      Nurturing a new perspective...
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'
import gsap from 'gsap'

const props = defineProps<{
  color: string
}>()

const stemRef = ref<SVGPathElement | null>(null)
const leavesRef = ref<SVGGElement | null>(null)
const flowerRef = ref<SVGGElement | null>(null)

onMounted(() => {
  const tl = gsap.timeline()

  // Animate Stem
  if (stemRef.value) {
    const length = stemRef.value.getTotalLength()
    gsap.set(stemRef.value, { strokeDasharray: length, strokeDashoffset: length })
    tl.to(stemRef.value, {
      strokeDashoffset: 0,
      duration: 1.5,
      ease: 'power1.out'
    })
  }

  // Animate Leaves
  if (leavesRef.value) {
    const leaves = leavesRef.value.querySelectorAll('.leaf')
    tl.to(leaves, {
      opacity: 1,
      scale: 1,
      duration: 0.8,
      stagger: 0.3,
      ease: 'back.out(2)'
    }, "-=0.5")
  }

  // Animate Flower Bloom
  if (flowerRef.value) {
    tl.to(flowerRef.value, {
      scale: 1,
      duration: 1,
      ease: 'elastic.out(1, 0.5)'
    }, "-=0.3")
  }
})
</script>

<style scoped>
.leaf {
  transform-origin: center bottom;
}
</style>
