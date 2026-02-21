<script setup lang="ts">
import AppSidebar from "@/components/AppSidebar.vue"
import SiteHeader from "@/components/SiteHeader.vue"
import {
  SidebarInset,
  SidebarProvider,
} from "@/components/ui/sidebar"
import { Card, CardHeader, CardTitle, CardDescription, CardContent } from '@/components/ui/card'
import { Badge } from '@/components/ui/badge'

const applications = [
  { company: "Google", role: "Frontend Engineer", status: "Interviewing", date: "2 days ago" },
  { company: "Meta", role: "Product Manager", status: "Applied", date: "1 week ago" },
  { company: "Amazon", role: "Software Engineer", status: "Rejected", date: "2 weeks ago" },
  { company: "Stripe", role: "Fullstack Developer", status: "Offer", date: "3 days ago" },
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
        <div class="grid gap-6">
          <div class="flex items-center justify-between">
            <div>
              <h1 class="text-2xl font-bold tracking-tight">Job Tracker</h1>
              <p class="text-muted-foreground">Monitor your application progress across companies</p>
            </div>
          </div>

          <div class="grid gap-4 md:grid-cols-2 lg:grid-cols-4">
            <Card v-for="app in applications" :key="app.company">
              <CardHeader>
                <div class="flex items-center justify-between">
                  <CardTitle class="text-lg">{{ app.company }}</CardTitle>
                  <Badge :variant="app.status === 'Rejected' ? 'destructive' : app.status === 'Offer' ? 'default' : 'secondary'">
                    {{ app.status }}
                  </Badge>
                </div>
                <CardDescription>{{ app.role }}</CardDescription>
              </CardHeader>
              <CardContent>
                <p class="text-xs text-muted-foreground">Applied {{ app.date }}</p>
              </CardContent>
            </Card>
          </div>
        </div>
      </div>
    </SidebarInset>
  </SidebarProvider>
</template>
