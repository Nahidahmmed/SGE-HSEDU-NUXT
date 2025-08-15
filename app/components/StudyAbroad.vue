<template>
  <div class="study-abroad max-w-[1200px] mx-auto px-4">
    <p
      class="text-3xl md:text-4xl lg:text-5xl font-semibold text-[#363B51] text-left leading-[60px] lg:mt-36 lg:w-[700px] md:w-auto w-full mt-72 mx-auto"
    >
      The Fastest and Easiest Way to Successfully Study Abroad
    </p>

    <!-- Desktop Grid -->
    <div class="hidden md:grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-6 mt-12">
      <div
        v-for="item in highlights"
        :key="item.id"
        class="rounded-xl p-6 flex flex-col items-center text-center bg-white w-[200px]"
        :style="{ boxShadow: '1px 1px 15px 2px #D4D4D4' }"
      >
        <img
          :src="item.image"
          :alt="item.text"
          width="50"
          height="50"
          class="mb-4 rounded-2xl"
        />
        <h3 class="text-2xl font-bold" :style="{ color: item.color }">
          {{ item.number }} +
        </h3>
        <p class="mt-2 text-sm font-thin text-[#7c808d]">
          {{ item.text }}
        </p>
      </div>
    </div>

    <!-- Mobile Slider -->
    <div class="block md:hidden mt-12 py-10">
      <ClientOnly>
        <Swiper
          :modules="[Pagination]"
          :pagination="{ clickable: true }"
          :space-between="20"
          :slides-per-view="1"
          class="pb-10"
        >
          <SwiperSlide v-for="item in highlights" :key="item.id">
            <div
              class="rounded-xl mt-5 p-6 flex flex-col items-center text-center bg-white w-[95%] mx-auto"
              :style="{ boxShadow: '-3px 8px 10px -3px #D4D4D4' }"
            >
              <img
                :src="item.image"
                :alt="item.text"
                width="80"
                height="80"
                class="mb-4 rounded"
              />
              <h3 class="text-2xl font-bold" :style="{ color: item.color }">
                {{ item.number }} +
              </h3>
              <p class="mt-2 text-sm font-thin text-[#7c808d]">
                {{ item.text }}
              </p>
            </div>
          </SwiperSlide>
        </Swiper>
      </ClientOnly>
    </div>
  </div>
</template>

<script setup>
import { Swiper, SwiperSlide } from 'swiper/vue'
import { Pagination } from 'swiper/modules'
import 'swiper/css'
import 'swiper/css/pagination'
import imgStudentsHelped from '@/assets/studentsHelped.png'
import imgGlobal from '@/assets/Global.png'
import imgInstitution from '@/assets/Institution.png'
import imgFlag from '@/assets/flag.png'
import imgUser from '@/assets/user.png'

const highlights = [
  { id: 1, image: imgStudentsHelped, text: 'Students Helped', number: '1.3M',   color: '#E72700' },
  { id: 2, image: imgGlobal,         text: 'Global Programs', number: '140,000', color: '#2563EB' },
  { id: 3, image: imgInstitution,    text: 'Institutions Globally', number: '1,500', color: '#16A34A' },
  { id: 4, image: imgFlag,           text: 'Nationalities',   number: 150,      color: '#F59E0B' },
  { id: 5, image: imgUser,           text: 'Years of Expertise', number: 10,     color: '#9333EA' },
]
</script>

<style scoped>
/* Local-only Swiper pagination styles using Tailwind via @apply */
.study-abroad :deep(.swiper-pagination) {
  @apply relative mt-[30px] bottom-0 text-center;
}
.study-abroad :deep(.swiper-pagination-bullet) {
  @apply bg-blue-600 opacity-40;
}
.study-abroad :deep(.swiper-pagination-bullet-active) {
  @apply opacity-100;
}
</style>
