<template>
  <div>
    <StudySplit
      orientation="right"
      eyebrow="INTERNATIONAL STUDENTS"
      title="Find Your Perfect Study Program"
      description="We’ve spent a decade perfecting a faster, easier, quality-first international study application process. Now, the world is yours to explore in just a few clicks."
      :bullets="bullets"
      cta-label="Try It Today"
      cta-href="/apply"
      :image-desktop="desktop"
      :image-mobile="mobile"
      image-alt="Study Abroad Illustration"
    />
  </div>
</template>

<script setup>
import { BookOpenIcon, IdentificationIcon, ChartBarIcon } from '@heroicons/vue/24/solid'
import StudySplit from './StudySplit.vue'
import desktop from '@/assets/study.png'
import mobile from '@/assets/study-boy.png'

const bullets = [
  { icon: BookOpenIcon, text: 'Easily apply to multiple programs' },
  { icon: IdentificationIcon, text: 'Find your perfect program from 140,000+ options in five top destinations' },
  { icon: ChartBarIcon, text: 'Higher chance of success with quality checks and AI technology' }
]
</script>
