<script setup lang="ts">
import { Card, CardContent, CardDescription, CardHeader, CardTitle, CardFooter } from '@/components/ui/card'
import { Badge } from '@/components/ui/badge'
import { Button } from '@/components/ui/button'
import { 
  IconBulb, 
  IconMicrophone, 
  IconBook, 
  IconBallpen,
  IconSparkles 
} from '@tabler/icons-vue'

definePageMeta({
  layout: "dashboard",
})

const tips = [
  {
    title: "The power of names",
    description: "Adding siblings, grandparents, or pets as supporting characters makes any story twice as engaging.",
    icon: IconBallpen,
    tag: "Creative",
    color: "bg-blue-500"
  },
  {
    title: "Audio storytelling",
    description: "Try reading the stories with funny voices for different characters. It creates memories that last a lifetime.",
    icon: IconMicrophone,
    tag: "Parenting",
    color: "bg-purple-500"
  },
  {
    title: "Learning moments",
    description: "Ask your child what they would do in the character's situation to encourage problem-solving and empathy.",
    icon: IconBulb,
    tag: "Educational",
    color: "bg-amber-500"
  },
  {
    title: "Theme consistency",
    description: "Stick to one theme for a 'multi-chapter' adventure over several nights to build anticipation.",
    icon: IconBook,
    tag: "Strategy",
    color: "bg-emerald-500"
  }
]
</script>

<template>
  <div class="flex flex-1 flex-col p-4 md:p-6 lg:p-8">
    <div class="max-w-5xl mx-auto w-full">
      <div class="mb-12">
        <h1 class="text-3xl font-bold tracking-tight">Storytelling Tips</h1>
        <p class="text-muted-foreground mt-2 text-lg">Pro tips to make your bedtime ritual even more magical.</p>
      </div>

      <div class="grid gap-6 md:grid-cols-2">
        <Card v-for="tip in tips" :key="tip.title" class="overflow-hidden group hover:shadow-xl transition-all duration-300 border-primary/10">
          <CardHeader>
            <div class="flex items-center justify-between mb-2">
              <div :class="[tip.color, 'p-3 rounded-2xl text-white shadow-lg transition-transform group-hover:scale-110']">
                 <component :is="tip.icon" class="size-6" />
              </div>
              <Badge variant="outline">{{ tip.tag }}</Badge>
            </div>
            <CardTitle class="text-xl pt-2">{{ tip.title }}</CardTitle>
            <CardDescription class="text-base leading-relaxed pt-2">
              {{ tip.description }}
            </CardDescription>
          </CardHeader>
          <CardFooter class="bg-muted/30 border-t pt-4">
            <Button variant="ghost" size="sm" class="text-primary hover:text-primary/80 p-0 h-auto font-bold uppercase tracking-widest text-[10px]">
              Learn more <IconSparkles class="ml-2 size-3" />
            </Button>
          </CardFooter>
        </Card>
      </div>

      <div class="mt-16 bg-gradient-to-br from-primary to-purple-600 rounded-[2.5rem] p-10 text-white relative overflow-hidden">
        <div class="absolute -right-20 -bottom-20 size-80 bg-white/10 rounded-full blur-3xl" />
        <div class="relative z-10 flex flex-col md:flex-row items-center gap-10">
          <div class="flex-1 text-center md:text-left">
            <h2 class="text-3xl font-bold mb-4">Want a custom universe?</h2>
            <p class="text-white/80 text-lg mb-8">Tell us about your child's unique obsession and we might add a special theme just for them.</p>
            <Button variant="secondary" class="bg-white text-primary hover:bg-white/90 rounded-full px-8 py-6 text-lg font-bold">
              Submit Theme Idea
            </Button>
          </div>
          <div class="size-48 bg-white/20 backdrop-blur-xl rounded-[3rem] flex items-center justify-center p-8 rotate-3 shadow-2xl">
            <IconSparkles class="size-full text-white animate-pulse" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
