<script setup lang="ts">
import AppSidebar from "@/components/AppSidebar.vue"
import SiteHeader from "@/components/SiteHeader.vue"
import {
  SidebarInset,
  SidebarProvider,
} from "@/components/ui/sidebar"
import { Card, CardHeader, CardTitle, CardDescription, CardContent, CardFooter } from '@/components/ui/card'
import { Button } from '@/components/ui/button'
import { Input } from '@/components/ui/input'
import { Label } from '@/components/ui/label'
import { IconSparkles } from '@tabler/icons-vue'

const isLoading = ref(false)

function handleGenerate() {
  isLoading.value = true
  setTimeout(() => {
    isLoading.value = false
    navigateTo('/dashboard/cvs')
  }, 2000)
}
</script>

<template>
  <SidebarProvider
    :style=" {
      '--sidebar-width': 'calc(var(--spacing) * 72)',
      '--header-height': 'calc(var(--spacing) * 12)',
    }"
  >
    <AppSidebar variant="inset" />
    <SidebarInset>
      <SiteHeader />
      <div class="flex flex-1 flex-col p-4 md:p-6">
        <div class="max-w-2xl mx-auto w-full">
          <div class="mb-8">
            <h1 class="text-3xl font-bold tracking-tight">Create New Resume</h1>
            <p class="text-muted-foreground mt-2">Personalize your professional story for your dream role.</p>
          </div>

          <Card>
            <CardHeader>
              <CardTitle>Basic Information</CardTitle>
              <CardDescription>Tell us about the role you are applying for.</CardDescription>
            </CardHeader>
            <CardContent class="grid gap-4">
              <div class="grid gap-2">
                <Label for="role">Target Role</Label>
                <Input id="role" placeholder="e.g. Senior Frontend Engineer" />
              </div>
              <div class="grid gap-2">
                <Label for="company">Target Company</Label>
                <Input id="company" placeholder="e.g. Google" />
              </div>
              <div class="grid gap-2">
                <Label for="focus">Key Focus (Optional)</Label>
                <Input id="focus" placeholder="e.g. React, TypeScript, Performance optimization" />
              </div>
            </CardContent>
            <CardFooter>
              <Button class="w-full" :disabled="isLoading" @click="handleGenerate">
                <IconSparkles v-if="!isLoading" class="mr-2 h-4 w-4" />
                <span v-else class="mr-2 h-4 w-4 animate-spin">
                   <svg
                    xmlns="http://www.w3.org/2000/svg"
                    width="24"
                    height="24"
                    viewBox="0 0 24 24"
                    fill="none"
                    stroke="currentColor"
                    stroke-width="2"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    class="lucide lucide-loader-2"
                  >
                    <path d="M21 12a9 9 0 1 1-6.219-8.56" />
                  </svg>
                </span>
                {{ isLoading ? 'AI is Crafting Your Story...' : 'Generate AI Optimized Resume' }}
              </Button>
            </CardFooter>
          </Card>
        </div>
      </div>
    </SidebarInset>
  </SidebarProvider>
</template>
