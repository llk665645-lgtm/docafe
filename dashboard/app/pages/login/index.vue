<script lang="ts">
export const description = "A two column login page with a cover image."
</script>

<script setup lang="ts">
import LoginForm from "@/components/login-02/components/LoginForm.vue"
import LogoIcon from "@/components/LogoIcon.vue"
</script>

<template>
  <div class="grid min-h-svh lg:grid-cols-2">
    <div class="flex flex-col gap-4 p-6 md:p-10 bg-background overflow-y-auto">
      <div class="flex justify-center gap-2 md:justify-start">
        <NuxtLink to="/" class="flex items-center gap-3 font-bold group">
          <div class="flex h-10 w-10 items-center justify-center rounded-xl bg-primary text-white shadow-lg transition-transform group-hover:scale-105">
            <LogoIcon class="size-6 stroke-white fill-white" />
          </div>
          <span class="text-xl tracking-tight text-foreground">Story<span class="text-primary italic">Me</span></span>
        </NuxtLink>
      </div>
      <div class="flex flex-1 items-center justify-center">
        <div class="w-full max-w-xs">
          <LoginForm />
        </div>
      </div>
    </div>
    <div class="bg-muted relative hidden lg:block overflow-hidden">
      <img
        src="/images/themes/ai-generated-3d-water.jpg"
        alt="Magical Water Background"
        class="absolute inset-0 h-full w-full object-cover opacity-90"
      >
      <div class="absolute inset-0 bg-gradient-to-l from-transparent via-transparent to-white/10" />
    </div>
  </div>
</template>
