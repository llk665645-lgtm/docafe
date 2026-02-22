<script setup lang="ts">
import { Card, CardContent, CardDescription, CardHeader, CardTitle, CardFooter } from '@/components/ui/card'
import { Button } from '@/components/ui/button'
import { Input } from '@/components/ui/input'
import { Label } from '@/components/ui/label'
import { 
  IconHelp, 
  IconMail, 
  IconMessageCircle, 
  IconBook,
  IconArrowRight
} from '@tabler/icons-vue'

definePageMeta({
  layout: "dashboard",
})

const faqs = [
  {
    question: "How do I create a new story?",
    answer: "Go to the 'My Stories' page and click on 'Create New Story'. You'll then be able to enter your child's name, interests, and choose a theme."
  },
  {
    question: "Can I print the stories?",
    answer: "Yes! You can download high-quality PDFs of your stories from the Gallery and print them at home to create your own physical storybook."
  },
  {
    question: "What are AI Credits?",
    answer: "Each story generation costs 1 AI credit. Your subscription includes a monthly allowance of credits, and you can always top up if you need more magic."
  },
  {
    question: "Are the stories safe for kids?",
    answer: "Absolutely. Our AI is specifically tuned to create child-friendly, age-appropriate content across all our fairytale worlds."
  }
]
</script>

<template>
  <div class="flex flex-1 flex-col p-4 md:p-6 lg:p-8">
    <div class="max-w-4xl mx-auto w-full">
      <div class="text-center mb-12">
        <h1 class="text-3xl font-bold tracking-tight mb-4">How can we help?</h1>
        <p class="text-muted-foreground text-lg">Find answers to common questions or reach out to our team of wizards.</p>
      </div>

      <div class="grid gap-8 md:grid-cols-2 mb-12">
        <Card class="border-primary/20 bg-primary/5">
          <CardHeader>
            <div class="size-12 rounded-2xl bg-primary/10 flex items-center justify-center mb-4">
              <IconMail class="size-6 text-primary" />
            </div>
            <CardTitle>Email Support</CardTitle>
            <CardDescription>Get in touch with our support team via email.</CardDescription>
          </CardHeader>
          <CardContent>
            <p class="text-sm">We usually respond within 24 hours to all parental queries.</p>
          </CardContent>
          <CardFooter>
            <Button variant="outline" class="w-full">contact@storyme.com</Button>
          </CardFooter>
        </Card>

        <Card class="border-purple-500/20 bg-purple-500/5">
          <CardHeader>
            <div class="size-12 rounded-2xl bg-purple-500/10 flex items-center justify-center mb-4">
              <IconMessageCircle class="size-6 text-purple-600" />
            </div>
            <CardTitle>Community Chat</CardTitle>
            <CardDescription>Join our community of parents and educators.</CardDescription>
          </CardHeader>
          <CardContent>
            <p class="text-sm">Share stories, tips, and get advice from other magical storytellers.</p>
          </CardContent>
          <CardFooter>
            <Button variant="outline" class="w-full">Join Discord</Button>
          </CardFooter>
        </Card>
      </div>

      <div class="space-y-6">
        <h2 class="text-2xl font-bold flex items-center gap-2 mb-6">
          <IconHelp class="size-6 text-primary" /> Frequently Asked Questions
        </h2>
        
        <div class="grid gap-4">
          <Card v-for="faq in faqs" :key="faq.question" class="overflow-hidden">
            <CardHeader class="p-0">
               <details class="group">
                 <summary class="flex items-center justify-between p-6 cursor-pointer list-none font-bold text-lg hover:bg-muted/30 transition-colors">
                   {{ faq.question }}
                   <IconArrowRight class="size-5 transition-transform group-open:rotate-90" />
                 </summary>
                 <div class="px-6 pb-6 text-muted-foreground leading-relaxed animate-in fade-in slide-in-from-top-1 duration-300">
                   {{ faq.answer }}
                 </div>
               </details>
            </CardHeader>
          </Card>
        </div>
      </div>

      <div class="mt-16 text-center pt-12 border-t">
        <IconBook class="size-12 text-muted-foreground/30 mx-auto mb-4" />
        <h3 class="font-bold text-xl mb-2">Still need help?</h3>
        <p class="text-muted-foreground mb-6">Our documentation has full guides on every feature.</p>
        <Button class="rounded-full px-8">Visit Documentation Center</Button>
      </div>
    </div>
  </div>
</template>
