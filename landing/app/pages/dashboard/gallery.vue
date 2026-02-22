<script setup lang="ts">
import { Card, CardContent, CardFooter } from '@/components/ui/card'
import { Badge } from '@/components/ui/badge'
import { Button } from '@/components/ui/button'
import { IconDownload, IconShare, IconEye } from '@tabler/icons-vue'

definePageMeta({
  layout: "dashboard",
})

const galleryItems = [
  { 
    id: 1, 
    title: "The Brave Little Dino", 
    theme: "Dino", 
    child: "Alex", 
    date: "Feb 18, 2026",
    image: "/images/themes/ai-generated-3d-water.jpg" // Placeholder until real images are present
  },
  { 
    id: 2, 
    title: "Starry Night Adventure", 
    theme: "Space", 
    child: "Sophia", 
    date: "Feb 15, 2026",
    image: "/images/themes/ai-generated-3d-water.jpg"
  },
  { 
    id: 3, 
    title: "The Magic Forest", 
    theme: "Forest", 
    child: "Alex", 
    date: "Feb 12, 2026",
    image: "/images/themes/ai-generated-3d-water.jpg"
  },
  { 
    id: 4, 
    title: "Underwater Kingdom", 
    theme: "Ocean", 
    child: "Leo", 
    date: "Feb 10, 2026",
    image: "/images/themes/ai-generated-3d-water.jpg"
  },
  { 
    id: 5, 
    title: "Heroic Skies", 
    theme: "Super", 
    child: "Sophia", 
    date: "Feb 08, 2026",
    image: "/images/themes/ai-generated-3d-water.jpg"
  },
  { 
    id: 6, 
    title: "Enchanted Fairytale", 
    theme: "Magic", 
    child: "Leo", 
    date: "Feb 05, 2026",
    image: "/images/themes/ai-generated-3d-water.jpg"
  },
]
</script>

<template>
  <div class="flex flex-1 flex-col p-4 md:p-6 lg:p-8">
    <div class="max-w-7xl mx-auto w-full">
      <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 mb-8">
        <div>
          <h1 class="text-3xl font-bold tracking-tight">Gallery</h1>
          <p class="text-muted-foreground mt-2">Browse the magical illustrations from your family's stories.</p>
        </div>
        <div class="flex gap-2">
          <Button variant="outline">Filter by Child</Button>
          <Button variant="outline">All Themes</Button>
        </div>
      </div>

      <div class="grid gap-6 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
        <Card v-for="item in galleryItems" :key="item.id" class="group overflow-hidden border-0 bg-transparent shadow-none hover:shadow-2xl hover:shadow-primary/10 transition-all duration-500">
          <div class="relative aspect-[4/5] rounded-[2rem] overflow-hidden bg-muted">
            <img 
              :src="item.image" 
              :alt="item.title"
              class="h-full w-full object-cover transition-transform duration-700 group-hover:scale-110"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-black/80 via-black/20 to-transparent opacity-0 group-hover:opacity-100 transition-opacity duration-500 flex flex-col justify-end p-6">
              <div class="flex gap-2 mb-4">
                <Button size="icon" variant="secondary" class="rounded-full bg-white/20 backdrop-blur-md border-0 text-white hover:bg-white/40">
                  <IconDownload class="size-4" />
                </Button>
                <Button size="icon" variant="secondary" class="rounded-full bg-white/20 backdrop-blur-md border-0 text-white hover:bg-white/40">
                  <IconShare class="size-4" />
                </Button>
                <Button size="icon" variant="secondary" class="rounded-full bg-white/20 backdrop-blur-md border-0 text-white hover:bg-white/40">
                  <IconEye class="size-4" />
                </Button>
              </div>
            </div>
            <div class="absolute top-4 left-4">
              <Badge variant="secondary" class="bg-white/80 backdrop-blur-sm border-0 text-primary font-bold">
                {{ item.theme }}
              </Badge>
            </div>
          </div>
          <CardHeader class="px-2 pt-4 pb-0">
            <h3 class="font-bold text-lg leading-tight line-clamp-1">{{ item.title }}</h3>
            <p class="text-xs text-muted-foreground">For {{ item.child }} • {{ item.date }}</p>
          </CardHeader>
        </Card>
      </div>
    </div>
  </div>
</template>
