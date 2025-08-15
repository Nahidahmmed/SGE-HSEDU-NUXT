
<template>
  <section class="w-full">
    <div class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8 py-14 lg:py-20">
      <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 lg:gap-12">
        <!-- Left intro -->
        <div class="lg:col-span-4 text-left">
          <p class="text-[#FF6A3D] text-sm font-semibold tracking-wide">{{ eyebrow }}</p>
          <h2 class="mt-3 text-3xl sm:text-4xl font-extrabold text-[#202637] leading-tight">
            {{ heading }}
          </h2>
          <p class="mt-4 text-[#5B6275] whitespace-pre-line">
            {{ blurb }}
          </p>
        </div>

        <!-- Right accordions -->
        <div class="lg:col-span-8 space-y-4">
          <div
            v-for="(item, i) in items"
            :key="i"
            class="rounded-xl border border-transparent bg-[#FFF3F0] hover:border-[#f0d9d9] transition"
          >
            <button
              type="button"
              :aria-expanded="open === i"
              :aria-controls="`faq-panel-${i}`"
              @click="toggle(i)"
              class="w-full flex items-center justify-between gap-4 px-5 sm:px-6 py-4 sm:py-5 text-left"
            >
              <span class="text-base sm:text-lg font-semibold text-[#434A63]">
                {{ item.q }}
              </span>
              <ChevronDownIcon
                class="w-5 h-5 shrink-0 text-[#434A63] transition-transform"
                :class="open === i ? 'rotate-180' : 'rotate-0'"
              />
            </button>

            <div
              :id="`faq-panel-${i}`"
              class="grid transition-[grid-template-rows,opacity] duration-300 ease-out"
              :class="open === i ? 'grid-rows-[1fr] opacity-100' : 'grid-rows-[0fr] opacity-0'"
            >
              <div class="overflow-hidden">
                <div class="px-5 font-thin sm:px-6 pb-5 sm:pb-6 text-[#434A63] leading-7">
                  {{ item.a }}
                </div>
              </div>
            </div>
          </div>
        </div>
        <!-- /Right -->
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { ChevronDownIcon } from '@heroicons/vue/24/solid'

type QA = { q: string; a: string }

const props = withDefaults(defineProps<{
  eyebrow?: string
  heading?: string
  blurb?: string
  items?: QA[]
}>(), {
  eyebrow: "FAQ’s",
  heading: "Got Questions? We Have Answers",
  blurb: `Still wondering about studying abroad, and how HSEDU can get you there?
Read these answers to our most commonly asked questions.`,
  items: () => ([
    {
      q: "How can I find my dream program?",
      a: "It couldn’t be easier! Register for a free HSEDU account, then take a few short minutes to tell us about your educational goals and set up your profile. Our platform will suggest study programs just for your needs, and you’ll have full access to explore the 140,000+ programs available through our AI-guided search."
    },
    { q: "How do I apply once I’ve found the right program?", a: "Complete your profile, upload documents, and submit in one place. We’ll guide you through each step." },
    { q: "Why should I use HSEDU?", a: "Faster applications, quality checks, expert support, and better outcomes." },
    { q: "Which countries can I apply to study in?", a: "Choose from top destinations including the US, UK, Canada, Australia, and more." },
    { q: "I’ve applied, so what’s next?", a: "Track status, get notifications, and manage offers right from your dashboard." }
  ])
})

const open = ref<number>(0) // first open by default
const toggle = (i: number) => {
  open.value = open.value === i ? -1 : i
}
</script>
