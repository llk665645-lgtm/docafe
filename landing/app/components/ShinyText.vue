
<script setup lang="ts">
import { computed } from 'vue';

interface ShinyTextProps {
  text: string;
  disabled?: boolean;
  speed?: number;
  className?: string;
  shimmerColor?: string;
}

const props = withDefaults(defineProps<ShinyTextProps>(), {
  text: '',
  disabled: false,
  speed: 5,
  className: '',
  shimmerColor: 'rgba(255, 255, 255, 0.8)'
});

const animationDuration = computed(() => `${props.speed}s`);
</script>

<template>
  <div
    :class="`bg-clip-text inline-block ${!props.disabled ? 'animate-shine' : ''} ${props.className}`"
    :style="{
      backgroundImage: `linear-gradient(120deg, transparent 40%, ${props.shimmerColor} 50%, transparent 60%)`,
      backgroundSize: '200% 100%',
      WebkitBackgroundClip: 'text',
      animationDuration: animationDuration,
    }"
  >
    {{ props.text }}
  </div>
</template>

<style scoped>
@keyframes shine {
  0% {
    background-position: 100%;
  }
  100% {
    background-position: -100%;
  }
}

.animate-shine {
  animation: shine 5s linear infinite;
}
</style>
