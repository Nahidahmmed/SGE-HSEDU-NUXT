<template>
  <section :class="['max-w-[1200px] mx-auto px-4 py-16', className]">
    <div :class="['flex flex-col items-center gap-10', dirClass]">
      <!-- Image Section -->
      <div class="w-full lg:w-1/2">
        <!-- Mobile image -->
        <div class="relative w-full aspect-square sm:aspect-[4/3] block lg:hidden">
          <img
            :src="imageMobile"
            :alt="imageAlt"
            class="object-contain w-full h-full"
            loading="eager"
          />
        </div>

        <!-- Desktop image -->
        <div class="relative w-full aspect-square sm:aspect-[4/3] hidden lg:block">
          <img
            :src="imageDesktop"
            :alt="imageAlt"
            class="object-contain w-full h-full"
            loading="eager"
          />
        </div>
      </div>

      <!-- Text Section -->
      <div class="w-full lg:w-1/2 text-left space-y-6">
        <p v-if="eyebrow" class="text-sm text-[#E72700] font-semibold tracking-widest">
          {{ eyebrow }}
        </p>

        <h2 v-if="title" class="text-3xl md:text-4xl font-bold text-[#363B51]">
          {{ title }}
        </h2>

        <p v-if="description" class="text-[#363B51]">
          {{ description }}
        </p>

        <div v-if="bullets?.length" class="space-y-4">
          <div
            v-for="(b, i) in bullets"
            :key="i"
            class="flex items-center gap-3"
          >
            <!-- Expecting b.icon to be a Vue component (e.g., BookOpenIcon) -->
            <component
              v-if="b.icon"
              :is="b.icon"
              class="w-7 h-7 text-[#E72700]"
            />
            <span class="text-[#363B51]">{{ b.text }}</span>
          </div>
        </div>

        <a
          v-if="ctaLabel"
          :href="ctaHref"
          class="inline-block mt-2 bg-[#EB401E] text-white px-6 py-2 rounded-lg hover:bg-[#d61f00] transition duration-300"
        >
          {{ ctaLabel }}
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
import { computed } from 'vue'

const props = defineProps({
  orientation: { type: String, default: 'right' }, // 'left' | 'right'
  eyebrow: { type: String, default: '' },
  title: { type: String, default: '' },
  description: { type: String, default: '' },

  /**
   * bullets: Array<{ icon?: Component, text: string }>
   * Example in parent:
   *   import { BookOpenIcon } from '@heroicons/vue/24/solid'
   *   const bullets = [{ icon: BookOpenIcon, text: '...' }]
   */
  bullets: { type: Array, default: () => [] },

  ctaLabel: { type: String, default: 'Try It Today' },
  ctaHref: { type: String, default: '#' },

  // Image paths: if from /public, pass '/assets/...' directly.
  // If from /assets, import in parent and pass the imported URL.
  imageDesktop: { type: String, required: true },
  imageMobile: { type: String, required: true },
  imageAlt: { type: String, default: '' },

  // optional extra classes for the <section>
  className: { type: String, default: '' },
})

const dirClass = computed(() =>
  props.orientation === 'left' ? 'lg:flex-row' : 'lg:flex-row-reverse'
)
</script>
