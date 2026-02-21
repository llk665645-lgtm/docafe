<script setup lang="ts">
import AppSidebar from "@/components/AppSidebar.vue"
import SiteHeader from "@/components/SiteHeader.vue"
import {
  SidebarInset,
  SidebarProvider,
} from "@/components/ui/sidebar"
import { Card, CardHeader, CardTitle, CardDescription, CardContent } from '@/components/ui/card'
import { Button } from '@/components/ui/button'
import { Input } from '@/components/ui/input'
import { Label } from '@/components/ui/label'
import { IconSparkles } from '@tabler/icons-vue'
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
        <div class="max-w-4xl mx-auto w-full">
          <div class="mb-8 text-center">
            <h1 class="text-3xl font-bold tracking-tight">ATS Match Analysis</h1>
            <p class="text-muted-foreground mt-2">Upload your resume and the job description to get a match score and optimization tips.</p>
          </div>

          <div class="grid gap-6">
            <Card>
              <CardHeader>
                <CardTitle>Analysis Input</CardTitle>
                <CardDescription>Paste the job description and select your resume</CardDescription>
              </CardHeader>
              <CardContent class="grid gap-4">
                <div class="grid gap-2">
                  <Label for="resume">Select Resume</Label>
                  <select id="resume" class="flex h-10 w-full rounded-md border border-input bg-background px-3 py-2 text-sm ring-offset-background file:border-0 file:bg-transparent file:text-sm file:font-medium placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50">
                    <option>Frontend Engineer Resume</option>
                    <option>Product Manager Profile</option>
                  </select>
                </div>
                <div class="grid gap-2">
                  <Label for="jd">Job Description</Label>
                  <textarea 
                    id="jd" 
                    placeholder="Paste the job description here..."
                    class="flex min-h-[200px] w-full rounded-md border border-input bg-background px-3 py-2 text-sm ring-offset-background placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:cursor-not-allowed disabled:opacity-50"
                  ></textarea>
                </div>
                <Button class="w-full">
                  <IconSparkles class="mr-2 h-4 w-4" /> Analyze Match
                </Button>
              </CardContent>
            </Card>
          </div>
        </div>
      </div>
    </SidebarInset>
  </SidebarProvider>
</template>
