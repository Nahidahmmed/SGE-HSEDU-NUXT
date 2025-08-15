<!-- components/UniversityCard.vue -->
<template>
  <article
    class="rounded-2xl overflow-hidden bg-white shadow-sm ring-1 ring-gray-200 hover:shadow-md transition w-[340px] mx-auto"
  >
    <!-- Cover -->
    <div class="relative lg:w-[340px] md:w-[340px] w-full h-[225px]">
      <!-- Use Nuxt Image if available -->
      <NuxtImg
        v-if="hasNuxtImage"
        :src="item.cover"
        alt="`${item.name} cover`"
        class="absolute inset-0 w-full h-full object-cover"
        :sizes="sizes"
        :preload="item.id <= 6"
        format="webp"
      />
      <!-- Fallback to plain <img> if @nuxt/image is not installed -->
      <img
        v-else
        :src="item.cover"
        :alt="`${item.name} cover`"
        class="absolute inset-0 w-full h-full object-cover"
        loading="eager"
        :fetchpriority="item.id <= 6 ? 'high' : 'auto'"
        decoding="async"
      />

      <div class="absolute top-1 left-1">
        <Button color="red" text="Featured" />
      </div>
    </div>

    <!-- Body -->
    <div class="p-4 sm:p-5">
      <div class="flex items-start gap-3 sm:gap-4">
        <!-- Logo -->
        <NuxtImg
          v-if="hasNuxtImage"
          :src="item.logo"
          :alt="`${item.name} logo`"
          width="48"
          height="48"
          class="rounded-full shrink-0 object-cover w-10 h-10 sm:w-12 sm:h-12"
          format="webp"
        />
        <img
          v-else
          :src="item.logo"
          :alt="`${item.name} logo`"
          width="48"
          height="48"
          class="rounded-full shrink-0 object-cover w-10 h-10 sm:w-12 sm:h-12"
          loading="lazy"
          decoding="async"
        />

        <div class="min-w-0">
          <h3 class="text-base sm:text-lg font-semibold text-[#2a2f3e] leading-tight truncate">
            {{ item.name }}
          </h3>
          <p class="text-xs sm:text-sm text-gray-500 mt-0.5 truncate">
            {{ item.title }}
          </p>
        </div>
      </div>

      <p class="text-left text-sm text-gray-500 dark:text-gray-400 mt-3 sm:mt-4 line-clamp-3">
        {{ item.text }}
      </p>
    </div>
  </article>
</template>

<script setup lang="ts">
type Partner = {
  id: number
  name: string
  logo: string
  cover: string
  title: string
  text: string
}

const props = defineProps<{
  item: Partner
}>()

// Match Next.js `sizes` behavior
const sizes =
  '(max-width: 640px) 100vw, (max-width: 1024px) 50vw, (max-width: 1536px) 25vw, 25vw'

// If you have @nuxt/image installed, <NuxtImg> is globally available.
// If not, we fallback to <img>.
const hasNuxtImage = !!(getCurrentInstance()?.appContext.app.component as any)('NuxtImg')
</script>
