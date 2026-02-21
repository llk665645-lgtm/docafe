<template>
  <svg 
    viewBox="0 0 100 100" 
    fill="none" 
    xmlns="http://www.w3.org/2000/svg"
    v-bind="$attrs"
  >
    <!-- Book Pages / Cover -->
    <path 
      d="M15 65 C 15 65, 35 75, 50 65 C 65 75, 85 65, 85 65 V 25 C 85 25, 65 35, 50 25 C 35 35, 15 25, 15 25 Z" 
      class="stroke-current" 
      stroke-width="6" 
      stroke-linecap="round" 
      stroke-linejoin="round"
      fill="none"
    />
    
    <!-- Spine -->
    <path 
      d="M50 25 V 65" 
      class="stroke-current" 
      stroke-width="6" 
      stroke-linecap="round" 
      stroke-linejoin="round"
      fill="none"
    />

    <!-- Magic Star (Central) -->
    <path 
      d="M50 5 L 54 16 L 65 20 L 54 24 L 50 35 L 46 24 L 35 20 L 46 16 Z" 
      class="fill-current"
    />

    <!-- Small particles -->
    <circle cx="28" cy="15" r="3" class="fill-current" />
    <circle cx="72" cy="15" r="3" class="fill-current opacity-80" />
    <circle cx="82" cy="32" r="2" class="fill-current opacity-60" />
    <circle cx="18" cy="32" r="2" class="fill-current opacity-60" />
  </svg>
</template>
