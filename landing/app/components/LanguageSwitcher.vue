<script setup lang="ts">
const { locale, setLocale } = useI18n()

// Define available locales
const availableLocales = [
  { code: 'en', name: 'English' },
  { code: 'ru', name: 'Русский' }
]

function toggleLocale() {
  const newLocale = locale.value === 'ru' ? 'en' : 'ru'
  setLocale(newLocale)
}
</script>

<template>
  <button 
    @click="toggleLocale"
    class="px-4 py-2 rounded-lg bg-gray-200 hover:bg-gray-300 transition-colors text-gray-800 font-medium"
    aria-label="Switch language"
  >
    {{ locale === 'ru' ? 'EN' : 'RU' }}
  </button>
</template>
