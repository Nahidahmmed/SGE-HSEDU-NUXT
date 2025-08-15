<!-- components/GetStarted.vue -->
<template>
  <section class="w-full">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
      <h2 class="text-center text-2xl sm:text-3xl font-extrabold text-[#2a2f3e] mb-10">
        {{ title }}
      </h2>

      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 justify-items-center lg:justify-items-stretch mx-auto">
        <div
          v-for="(card, idx) in cards"
          :key="idx"
          class="flex flex-col bg-white rounded-2xl overflow-hidden w-full max-w-[440px] lg:w-[360px] mx-auto"
        >
          <div class="relative lg:w-[320px] md:w-[300px] w-[90%] mx-auto h-40 sm:h-48 lg:h-56">
            <img
              :src="card.image"
              :alt="card.alt"
              class="absolute inset-0 w-full h-full object-cover rounded-t-3xl lg:rounded-b-md md:rounded-b-md rounded-b-2xl"
              :loading="idx === 0 ? 'eager' : 'lazy'"
              decoding="async"
            />
          </div>

          <div class="flex flex-col flex-1 px-4 sm:px-5">
            <h3 class="text-xl lg:text-2xl pt-4 lg:pt-5 font-bold text-[#434A63]">
              {{ card.heading }}
            </h3>
            <p class="mt-2 text-[#5B6275] leading-relaxed flex-1 text-sm lg:text-base">
              {{ card.text }}
            </p>
            <a
              :href="card.href"
              class="my-4 lg:my-5 inline-block w-full text-center rounded-md bg-[#EB401E] text-white px-4 py-2 font-thin hover:bg-[#c81f00] transition"
            >
              {{ card.button }}
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
// Import images from ~/assets so Nuxt processes them
import started1 from '~/assets/started1.png'
import started2 from '~/assets/started2.png'
import started3 from '~/assets/started3.png'

type Card = {
  image: string
  alt: string
  heading: string
  text: string
  button: string
  href: string
}

const props = withDefaults(defineProps<{
  title?: string
  cards?: Card[]
}>(), {
  title: 'Get Started with HSEDU',
  cards: () => ([
    {
      image: started1,
      alt: 'Student',
      heading: 'Student',
      text: 'Are you a student looking to study in Canada, the US, the UK, Ireland, Australia, or Germany? Register to launch your journey now!',
      button: 'Sign Up for Free',
      href: '#'
    },
    {
      image: started2,
      alt: 'Recruitment Partner',
      heading: 'Recruitment Partner',
      text: 'Do you recruit and guide international students? Join our partner network and revolutionize your process!',
      button: 'Become a Recruitment Partner',
      href: '#'
    },
    {
      image: started3,
      alt: 'Partner School',
      heading: 'Partner School',
      text: 'Join 1,500+ global institutions on the HSEDU platform! Complete our contact form, and our Partner Relations team will be in touch soon.',
      button: 'Become a Partner Institution',
      href: '#'
    }
  ])
})
</script>
