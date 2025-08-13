<template>
  <div class="max-w-[1200px] mx-auto px-4 py-12 mt-20">
    <!-- Header -->
    <div class="flex items-center justify-between flex-wrap gap-4">
      <div>
        <h2 class="text-4xl font-bold text-[#292E3E]">
          What Our Students Have to Say
        </h2>
        <p class="mt-2 text-[#363B51]">
          Hear from real international students about their experience.
        </p>
      </div>

      <!-- Buttons (desktop only; visual only like your original) -->
      <div class="hidden lg:flex gap-3">
        <button class="bg-[#FFF9F8] p-4 rounded-2xl shadow-md hover:bg-gray-100 transition">
          <ChevronLeftIcon class="w-4 h-4 text-[#292E3E]" />
        </button>
        <button class="bg-[#FFF9F8] p-4 rounded-2xl shadow-md hover:bg-gray-100 transition">
          <ChevronRightIcon class="w-4 h-4 text-[#292E3E]" />
        </button>
      </div>
    </div>

    <!-- Desktop Grid -->
    <div class="hidden lg:grid grid-cols-2 gap-6 mt-10">
      <div
        v-for="review in reviews"
        :key="review.id"
        class="bg-[#FFF9F8] p-6 rounded-2xl shadow-sm flex flex-col justify-between h-full"
      >
        <!-- Content -->
        <div>
          <img
            :src="testimonialIcon"
            alt="Quote"
            width="50"
            height="50"
            class="w-10 h-auto object-contain"
          />
          <h1 class="text-xl md:text-2xl font-semibold text-left text-[#292E3E] mt-4">
            {{ review.title }}
          </h1>
          <p class="text-left text-[#363B51] mt-2">
            {{ review.text }}
          </p>
        </div>

        <!-- User Info -->
        <div class="flex items-center gap-3 pt-6">
          <img
            :src="review.userImage"
            :alt="review.user"
            width="50"
            height="50"
            class="w-12 h-12 rounded-full object-cover"
          />
          <p class="text-[#292E3E] font-medium">{{ review.user }}</p>
        </div>
      </div>
    </div>

    <!-- Mobile Slider -->
    <div class="block lg:hidden mt-10">
      <ClientOnly>
        <Swiper
          :modules="[Pagination]"
          :pagination="{ clickable: true }"
          :space-between="20"
          :slides-per-view="1"
          class="pb-12"
        >
          <SwiperSlide v-for="review in reviews" :key="review.id">
            <div class="bg-[#FFF9F8] p-6 rounded-2xl shadow-sm flex flex-col justify-between h-[400px]">
              <!-- Content -->
              <div>
                <img
                  :src="testimonialIcon"
                  alt="Quote"
                  width="50"
                  height="50"
                  class="w-10 h-auto object-contain"
                />
                <h1 class="text-xl md:text-2xl font-semibold text-left text-[#292E3E] mt-4">
                  {{ review.title }}
                </h1>
                <p class="text-left text-[#363B51] mt-2">
                  {{ review.text }}
                </p>
              </div>

              <!-- User Info -->
              <div class="flex items-center gap-3 pt-6">
                <img
                  :src="review.userImage"
                  :alt="review.user"
                  width="50"
                  height="50"
                  class="w-12 h-12 rounded-full object-cover"
                />
                <p class="text-[#292E3E] font-medium">{{ review.user }}</p>
              </div>
            </div>
          </SwiperSlide>
        </Swiper>
      </ClientOnly>
    </div>
  </div>
</template>

<script setup>
import { ChevronLeftIcon, ChevronRightIcon } from '@heroicons/vue/24/outline'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Pagination } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/pagination'

// ✅ Import images from /assets so Vite resolves them
import testimonialIcon from '@/assets/Testimonial Icon.png'
import user1 from '@/assets/user1.png'
import user2 from '@/assets/user2.png'

const reviews = [
  {
    id: 1,
    title: 'Like an answer from heaven',
    text:
      '“I tried [applying to institutions] and it took months, and months, and months for me to get an answer from a school. But then I stumbled upon HSEDU, and it was like an answer from heaven.”',
    user: 'Arabelle A.',
    userImage: user1,
  },
  {
    id: 2,
    title: 'All thanks to HSEDU',
    text:
      '“I wanted to make my parents proud, and they are proud. And it was all thanks to HSEDU.”',
    user: 'Krupali P.',
    userImage: user2,
  },
]
</script>

<style scoped>
/* Local-only Swiper pagination styles using Tailwind via @apply */
:deep(.swiper-pagination) {
  @apply relative mt-[30px] bottom-0 text-center;
}
:deep(.swiper-pagination-bullet) {
  @apply bg-blue-600 opacity-40;
}
:deep(.swiper-pagination-bullet-active) {
  @apply opacity-100;
}
</style>
