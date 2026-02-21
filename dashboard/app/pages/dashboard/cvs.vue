<script setup lang="ts">
import AppSidebar from "@/components/AppSidebar.vue"
import DataTable from "@/components/DataTable.vue"
import SiteHeader from "@/components/SiteHeader.vue"
import {
  SidebarInset,
  SidebarProvider,
} from "@/components/ui/sidebar"
import { Button } from '@/components/ui/button'
import { IconPlus } from '@tabler/icons-vue'

const cvs = [
  {
    id: 1,
    header: "Frontend Engineer Resume",
    type: "Tech",
    status: "Completed",
    target: "Google",
    limit: "98% Match",
    reviewer: "AI Assistant",
  },
  {
    id: 2,
    header: "Product Manager Profile",
    type: "Management",
    status: "Reviewing",
    target: "Meta",
    limit: "85% Match",
    reviewer: "AI Assistant",
  },
  {
    id: 3,
    header: "UX Designer Portfolio CV",
    type: "Design",
    status: "Completed",
    target: "Airbnb",
    limit: "92% Match",
    reviewer: "AI Assistant",
  },
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
      <div class="flex flex-1 flex-col">
        <div class="flex flex-col gap-4 py-4 md:gap-6 md:py-6">
          <div class="flex items-center justify-between px-4 lg:px-6">
            <div>
              <h1 class="text-2xl font-bold tracking-tight">My CVs</h1>
              <p class="text-muted-foreground">Manage and tailor your professional resumes</p>
            </div>
            <Button>
              <IconPlus class="mr-2 h-4 w-4" /> Create New CV
            </Button>
          </div>
          <DataTable :data="cvs" />
        </div>
      </div>
    </SidebarInset>
  </SidebarProvider>
</template>
