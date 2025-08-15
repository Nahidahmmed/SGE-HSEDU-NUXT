<template>
  <div>
    <StudySplit
      orientation="left"
      eyebrow="PARTNERS INSTITUTIONS"
      title="How We Help Partner Institutions"
      description="Manage documents, track statuses, and submit complete applications faster with our guided checks."
      :bullets="bulletsInstitutions"
      cta-label="Partner with Us"
      cta-href="/partners"
      :image-desktop="partner1"
      :image-mobile="partner1m"
      image-alt="Student with books"
    />

    <StudySplit
      orientation="right"
      eyebrow="RECRUITMENT PARTNERS"
      title="How We Help Recruitment Partners"
      description="We’ve spent a decade perfecting a faster, easier, quality-first international study application process. Now, the world is yours to explore in just a few clicks."
      :bullets="bulletsRecruitment"
      cta-label="Join Our Network"
      cta-href="/apply"
      :image-desktop="partner2"
      :image-mobile="partner2m"
      image-alt="Study Abroad Illustration"
    />
  </div>
</template>

<script setup lang="ts">
import StudySplit from '~/components/StudySplit.vue'
import {
  GlobeAltIcon,
  IdentificationIcon,
  UserCircleIcon,
  BookOpenIcon,
  CurrencyDollarIcon
} from '@heroicons/vue/24/outline'

// ✅ Import images from assets (Nuxt/Vite will hash & optimize)
import partner1 from '@/assets/partner1.png'
import partner1m from '@/assets/partner1m.png'
import partner2 from '@/assets/partner2.png'
import partner2m from '@/assets/partner2m.png'

type Bullet = {
  icon: any
  text: string
}

const bulletsInstitutions: Bullet[] = [
  { icon: GlobeAltIcon, text: 'Diversify your enrolment with students from 150+ nationalities' },
  { icon: IdentificationIcon, text: 'Receive higher quality applications and improve conversion by 10%' },
  { icon: UserCircleIcon, text: 'Leverage proven technology to save time and reduce manual processing by 40%' }
]

const bulletsRecruitment: Bullet[] = [
  { icon: BookOpenIcon, text: 'Access 140,000+ programs at 1,500+ academic institutions' },
  { icon: IdentificationIcon, text: 'Use AI-powered tools to benefit from HSEDU 95% application success rate' },
  { icon: CurrencyDollarIcon, text: 'Support students with extra built-in services, from language tests to student loans' }
]
</script>
