<template>
  <p ref="rootRef" :class="[className, 'flex', 'flex-wrap']">
    <span
      v-for="(segment, index) in elements"
      :key="index"
      class="inline-block opacity-0"
      :ref="el => { if (el) letterRefs[index] = el as HTMLElement }"
    >
      {{ segment === ' ' ? '\u00A0' : segment }}
      {{ animateBy === 'words' && index < elements.length - 1 ? '\u00A0' : '' }}
    </span>
  </p>
</template>

<script setup lang="ts">
import { ref, computed, onMounted, watch } from 'vue';
import gsap from 'gsap';

type AnimateBy = 'words' | 'letters';

interface BlurTextProps {
  text?: string;
  delay?: number;
  className?: string;
  animateBy?: AnimateBy;
  threshold?: number;
  onAnimationComplete?: () => void;
}

const props = withDefaults(defineProps<BlurTextProps>(), {
  text: '',
  delay: 200, // Initial delay before animation starts
  className: '',
  animateBy: 'words',
  threshold: 0.1,
});

const elements = computed(() => {
  if (props.animateBy === 'words') {
    return props.text.split(' ');
  }
  return props.text.split('');
});

const rootRef = ref<HTMLElement | null>(null);
const letterRefs = ref<HTMLElement[]>([]);

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => {
      if (entry.isIntersecting) {
        animateText();
        observer.unobserve(entry.target);
      }
    },
    { threshold: props.threshold }
  );

  if (rootRef.value) {
    observer.observe(rootRef.value);
  }
});

const animateText = () => {
  gsap.to(letterRefs.value, {
    opacity: 1,
    duration: 0.8,
    ease: 'power2.out',
    stagger: 0.1,
    delay: props.delay / 1000,
    onComplete: () => {
      if (props.onAnimationComplete) {
        props.onAnimationComplete();
      }
    }
  });
};

watch(() => props.text, () => {
  // Reset opacity if text changes and re-animate? 
  // For now, simpler implementation assumes text is static or component remounts.
  // If dynamic, we'd need to kill tweens and restart.
});
</script>
