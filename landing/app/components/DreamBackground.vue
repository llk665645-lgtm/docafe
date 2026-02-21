<template>
  <div class="fixed inset-0 z-[-1] overflow-hidden bg-gradient-to-b from-[#0F172A] via-[#1E293B] to-[#334155]">
    <!-- Central Radial Highlight -->
    <div class="absolute inset-0 bg-[radial-gradient(circle_at_50%_50%,rgba(255,255,255,0.03),transparent_70%)]" />

    <!-- Cute Drifting Clouds -->
    <div class="absolute inset-0 pointer-events-none opacity-20">
      <!-- Cloud 1 -->
      <div class="absolute top-[10%] left-[-10%] animate-drift-slow-1 blur-[2px]">
        <svg class="w-64 h-auto text-white" viewBox="0 0 24 24" fill="currentColor">
          <path d="M17.5,19c-3.037,0-5.5-2.463-5.5-5.5c0-0.101,0.006-0.201,0.012-0.3c-0.334,0.063-0.672,0.1-1.012,0.1 c-2.485,0-4.5-2.015-4.5-4.5c0-0.198,0.013-0.392,0.038-0.583C4.851,8.381,4,7.285,4,6c0-1.657,1.343-3,3-3c0.113,0,0.223,0.007,0.331,0.02 C8.006,1.261,9.615,0,11.5,0c2.14,0,3.929,1.554,4.359,3.6c0.37-0.064,0.75-0.1,1.141-0.1c3.037,0,5.5,2.463,5.5,5.5 c0,0.224-0.015,0.445-0.041,0.661C23.239,10.612,24,11.716,24,13c0,1.657-1.343,3-3,3c-0.148,0-0.292-0.011-0.432-0.032 C19.897,17.75,18.791,19,17.5,19z" />
        </svg>
      </div>
      <!-- Cloud 2 -->
      <div class="absolute top-[40%] right-[-15%] animate-drift-slow-2 blur-[3px]">
        <svg class="w-80 h-auto text-white" viewBox="0 0 24 24" fill="currentColor">
          <path d="M17.5,19c-3.037,0-5.5-2.463-5.5-5.5c0-0.101,0.006-0.201,0.012-0.3c-0.334,0.063-0.672,0.1-1.012,0.1 c-2.485,0-4.5-2.015-4.5-4.5c0-0.198,0.013-0.392,0.038-0.583C4.851,8.381,4,7.285,4,6c0-1.657,1.343-3,3-3c0.113,0,0.223,0.007,0.331,0.02 C8.006,1.261,9.615,0,11.5,0c2.14,0,3.929,1.554,4.359,3.6c0.37-0.064,0.75-0.1,1.141-0.1c3.037,0,5.5,2.463,5.5,5.5 c0,0.224-0.015,0.445-0.041,0.661C23.239,10.612,24,11.716,24,13c0,1.657-1.343,3-3,3c-0.148,0-0.292-0.011-0.432-0.032 C19.897,17.75,18.791,19,17.5,19z" />
        </svg>
      </div>
      <!-- Cloud 3 -->
      <div class="absolute top-[70%] left-[-20%] animate-drift-slow-3 blur-[4px]">
        <svg class="w-96 h-auto text-white" viewBox="0 0 24 24" fill="currentColor">
          <path d="M17.5,19c-3.037,0-5.5-2.463-5.5-5.5c0-0.101,0.006-0.201,0.012-0.3c-0.334,0.063-0.672,0.1-1.012,0.1 c-2.485,0-4.5-2.015-4.5-4.5c0-0.198,0.013-0.392,0.038-0.583C4.851,8.381,4,7.285,4,6c0-1.657,1.343-3,3-3c0.113,0,0.223,0.007,0.331,0.02 C8.006,1.261,9.615,0,11.5,0c2.14,0,3.929,1.554,4.359,3.6c0.37-0.064,0.75-0.1,1.141-0.1c3.037,0,5.5,2.463,5.5,5.5 c0,0.224-0.015,0.445-0.041,0.661C23.239,10.612,24,11.716,24,13c0,1.657-1.343,3-3,3c-0.148,0-0.292-0.011-0.432-0.032 C19.897,17.75,18.791,19,17.5,19z" />
        </svg>
      </div>
    </div>

    <!-- Soft Ambient Highlights (Blurred circles) -->
    <div class="absolute top-[10%] left-[-10%] w-[120%] h-[50%] bg-white/5 blur-[120px] rounded-[100%] animate-cloud-drift-1" />
    <div class="absolute top-[30%] right-[-10%] w-[100%] h-[40%] bg-white/10 blur-[90px] rounded-[100%] animate-cloud-drift-2" />
    <div class="absolute top-[55%] left-[5%] w-[90%] h-[35%] bg-white/15 blur-[60px] rounded-[100%] animate-cloud-drift-1" />
    
    <!-- Atmosphere Filter -->
    <div class="absolute inset-0 backdrop-blur-[1px] pointer-events-none" />
  </div>
</template>

<script setup lang="ts">
// Dream Background Component
</script>

<style scoped>
/* Tailwind v4 animation classes are picked up from main.css */
</style>
