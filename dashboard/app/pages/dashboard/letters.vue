<script setup lang="ts">
import AppSidebar from "@/components/AppSidebar.vue"
import SiteHeader from "@/components/SiteHeader.vue"
import {
  SidebarInset,
  SidebarProvider,
} from "@/components/ui/sidebar"
import { Card, CardHeader, CardTitle, CardDescription, CardContent, CardFooter } from '@/components/ui/card'
import { Button } from '@/components/ui/button'
import { IconPlus, IconCopy } from '@tabler/icons-vue'

const letters = [
  { id: 1, title: "Cover Letter - Google", role: "Frontend Engineer", date: "Feb 20, 2026" },
  { id: 2, title: "Cover Letter - Meta", role: "Product Manager", date: "Feb 18, 2026" },
  { id: 3, title: "General Cover Letter", role: "Software Engineer", date: "Feb 15, 2026" },
]
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
        <div class="flex items-center justify-between mb-6">
          <div>
            <h1 class="text-2xl font-bold tracking-tight">Cover Letters</h1>
            <p class="text-muted-foreground">AI-generated cover letters tailored for each role</p>
          </div>
          <Button>
            <IconPlus class="mr-2 h-4 w-4" /> Generate New
          </Button>
        </div>

        <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-3">
          <Card v-for="letter in letters" :key="letter.id">
            <CardHeader>
              <CardTitle>{{ letter.title }}</CardTitle>
              <CardDescription>{{ letter.role }}</CardDescription>
            </CardHeader>
            <CardContent>
              <p class="text-sm text-muted-foreground">{{ letter.date }}</p>
            </CardContent>
            <CardFooter class="flex justify-end gap-2">
              <Button variant="outline" size="sm">
                <IconCopy class="mr-2 h-4 w-4" /> Copy
              </Button>
              <Button size="sm">Edit</Button>
            </CardFooter>
          </Card>
        </div>
      </div>
    </SidebarInset>
  </SidebarProvider>
</template>
