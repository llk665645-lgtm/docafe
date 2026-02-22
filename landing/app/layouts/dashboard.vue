<script setup lang="ts">
import AppSidebar from "@/components/AppSidebar.vue"
import SiteHeader from "@/components/SiteHeader.vue"
import DreamBackground from "@/components/DreamBackground.vue"
import {
  SidebarInset,
  SidebarProvider,
} from "@/components/ui/sidebar"
</script>

<template>
  <SidebarProvider
    class="bg-transparent"
    :style=" {
      '--sidebar-width': 'calc(var(--spacing) * 72)',
      '--header-height': 'calc(var(--spacing) * 12)',
    }"
  >
    <DreamBackground />
    <AppSidebar variant="inset" class="bg-transparent" />
    <SidebarInset class="bg-transparent min-h-screen">
      <SiteHeader class="bg-transparent sticky top-0 z-30" />
      <div class="flex-1 overflow-auto">
        <slot />
      </div>
    </SidebarInset>
  </SidebarProvider>
</template>
