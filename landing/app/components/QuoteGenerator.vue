<template>
  <div class="w-full max-w-4xl mx-auto mt-12 p-8 rounded-3xl bg-white/50 backdrop-blur-xl border border-white/20 shadow-2xl overflow-hidden">
    <div class="flex flex-col gap-8">
      <!-- Mood Selector -->
      <div class="flex flex-wrap justify-center gap-4">
        <button
          v-for="mood in moods"
          :key="mood.id"
          @click="selectedMood = mood.id"
          class="group relative flex flex-col items-center gap-2 p-4 rounded-2xl transition-all duration-300"
          :class="[
            selectedMood === mood.id 
              ? 'bg-white shadow-lg scale-110 z-10' 
              : 'hover:bg-white/40 grayscale hover:grayscale-0'
          ]"
        >
          <div 
            class="w-12 h-12 flex items-center justify-center rounded-xl text-2xl transition-transform duration-500 group-hover:rotate-12"
            :style="{ backgroundColor: mood.color + '20', color: mood.color }"
          >
            <Icon :name="mood.icon" />
          </div>
          <span class="text-sm font-semibold text-brand-dark">{{ mood.label }}</span>
          
          <div 
            v-if="selectedMood === mood.id"
            class="absolute -bottom-1 left-1/2 -translate-x-1/2 w-1 h-1 rounded-full"
            :style="{ backgroundColor: mood.color }"
          />
        </button>
      </div>

      <!-- Action Button -->
      <div class="flex justify-center">
        <button
          @click="generateQuote"
          :disabled="isGenerating"
          class="relative group px-8 py-4 rounded-full bg-brand-dark text-white font-bold text-lg overflow-hidden transition-all hover:scale-105 active:scale-95 disabled:opacity-50"
        >
          <span class="relative z-10 flex items-center gap-2">
            <Icon v-if="isGenerating" name="svg-spinners:90-ring-with-bg" class="size-5" />
            <Icon v-else name="lucide:sparkles" class="size-5" />
            {{ isGenerating ? 'Finding Wisdom...' : 'Reveal My Quote' }}
          </span>
          <div 
            class="absolute inset-0 bg-gradient-to-r opacity-0 group-hover:opacity-100 transition-opacity duration-300"
            :style="{ backgroundImage: `linear-gradient(to right, ${currentMoodColor}40, ${currentMoodColor}80)` }"
          />
        </button>
      </div>

      <!-- Result Area -->
      <Transition
        enter-active-class="transition duration-500 ease-out"
        enter-from-class="opacity-0 translate-y-8 scale-95"
        enter-to-class="opacity-100 translate-y-0 scale-100"
        leave-active-class="transition duration-300 ease-in"
        leave-from-class="opacity-100 scale-100"
        leave-to-class="opacity-0 scale-95"
      >
        <div v-if="generatedQuote" class="relative mt-8 p-12 rounded-4xl bg-white shadow-inner overflow-hidden min-h-[300px] flex flex-col items-center justify-center text-center">
          <Icon name="lucide:quote" class="absolute top-8 left-8 size-12 opacity-10" :style="{ color: currentMoodColor }" />
          
          <blockquote class="relative z-10">
            <p class="text-3xl md:text-4xl font-serif italic text-brand-dark leading-snug">
              {{ generatedQuote.text }}
            </p>
            <footer class="mt-8 flex flex-col items-center gap-2">
              <span class="text-xl font-bold text-brand-dark">— {{ generatedQuote.author }} —</span>
              <span class="text-brand-gray font-medium tracking-wide uppercase text-[10px] opacity-60">
                Wisdom of the Greats
              </span>
            </footer>
          </blockquote>

          <!-- Card Actions -->
          <div class="mt-12 flex flex-wrap justify-center gap-4 relative z-10">
            <button class="flex items-center gap-2 px-4 py-2 rounded-xl bg-brand-light hover:bg-white border border-brand-dark/5 transition-colors text-sm font-semibold">
              <Icon name="lucide:download" class="size-4" />
              Save as Image
            </button>
            <button class="flex items-center gap-2 px-4 py-2 rounded-xl bg-brand-light hover:bg-white border border-brand-dark/5 transition-colors text-sm font-semibold">
              <Icon name="lucide:share-2" class="size-4" />
              Share
            </button>
            <button class="flex items-center gap-2 px-4 py-2 rounded-xl bg-brand-light hover:bg-white border border-brand-dark/5 transition-colors text-sm font-semibold">
              <Icon name="lucide:copy" class="size-4" />
              Copy Text
            </button>
          </div>
        </div>
      </Transition>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

interface Mood {
  id: string
  label: string
  icon: string
  color: string
}

interface Quote {
  text: string
  author: string
}

const moods: Mood[] = [
  { id: 'motivation', label: 'Motivation', icon: 'lucide:rocket', color: '#f43f5e' },
  { id: 'inspiration', label: 'Inspiration', icon: 'lucide:lightbulb', color: '#8b5cf6' },
  { id: 'calm', label: 'Calm', icon: 'lucide:wind', color: '#10b981' },
  { id: 'confidence', label: 'Confidence', icon: 'lucide:shield', color: '#0ea5e9' },
  { id: 'love', label: 'Love', icon: 'lucide:heart', color: '#ec4899' },
]

const selectedMood = ref<string>(moods[0]?.id || 'motivation')
const isGenerating = ref(false)
const generatedQuote = ref<Quote | null>(null)

const currentMoodColor = computed(() => {
  const mood = moods.find(m => m.id === selectedMood.value)
  return mood ? mood.color : '#ba445b'
})

const quotes: Record<string, Quote[]> = {
  motivation: [
    { text: "It does not matter how slowly you go as long as you do not stop.", author: "Confucius" },
    { text: "The only way to do great work is to love what you do.", author: "Steve Jobs" },
    { text: "Success is not final, failure is not fatal: it is the courage to continue that counts.", author: "Winston Churchill" },
    { text: "What you get by achieving your goals is not as important as what you become by achieving your goals.", author: "Zig Ziglar" }
  ],
  inspiration: [
    { text: "The best way to predict the future is to invent it.", author: "Alan Kay" },
    { text: "Everything you can imagine is real.", author: "Pablo Picasso" },
    { text: "The only limit to our realization of tomorrow will be our doubts of today.", author: "Franklin D. Roosevelt" },
    { text: "Life is what happens when you're busy making other plans.", author: "John Lennon" }
  ],
  calm: [
    { text: "Empty your mind, be formless, shapeless — like water.", author: "Bruce Lee" },
    { text: "Peace comes from within. Do not seek it without.", author: "Buddha" },
    { text: "The soul always knows what to do to heal itself. The challenge is to silence the mind.", author: "Caroline Myss" },
    { text: "He who is of a calm and happy nature will hardly feel the pressure of age.", author: "Plato" }
  ],
  confidence: [
    { text: "Whether you think you can or you think you can't, you're right.", author: "Henry Ford" },
    { text: "No one can make you feel inferior without your consent.", author: "Eleanor Roosevelt" },
    { text: "With confidence, you have won before you have started.", author: "Marcus Garvey" },
    { text: "Believe in yourself! Have faith in your abilities!", author: "Norman Vincent Peale" }
  ],
  love: [
    { text: "Love all, trust a few, do wrong to none.", author: "William Shakespeare" },
    { text: "The greatest thing you'll ever learn is just to love and be loved in return.", author: "Eden Ahbez" },
    { text: "Where there is love there is life.", author: "Mahatma Gandhi" },
    { text: "Being deeply loved by someone gives you strength, while loving someone deeply gives you courage.", author: "Lao Tzu" }
  ]
}

async function generateQuote() {
  isGenerating.value = true
  generatedQuote.value = null
  
  // Simulate AI selection/generation delay
  await new Promise(resolve => setTimeout(resolve, 1500))
  
  const moodQuotes = quotes[selectedMood.value] || []
  const randomIndex = Math.floor(Math.random() * moodQuotes.length)
  const selectedQuote = moodQuotes[randomIndex] || { text: "Stay positive and keep moving forward.", author: "Unknown" }
  
  generatedQuote.value = selectedQuote
  
  isGenerating.value = false
}
</script>
