<template>
  <nav class="w-full bg-white fixed top-0 left-0 z-50">
    <div class="max-w-7xl mx-auto flex items-center px-4 py-3">
      <!-- Left: Hamburger + Logo -->
      <div class="flex items-center gap-3">
        <!-- Mobile Hamburger -->
        <button
          class="lg:hidden"
          @click="menuOpen = !menuOpen"
          aria-label="Toggle menu"
        >
          <component
            :is="menuOpen ? XMarkIcon : Bars3Icon"
            class="w-7 h-7 text-gray-700"
          />
        </button>

        <!-- Logo -->
        <NuxtLink to="/" class="text-xl font-bold text-[#E72700]">
          HSEDU
        </NuxtLink>
      </div>

      <!-- Desktop Nav -->
      <div class="hidden lg:flex items-center gap-10 ml-auto">
        <NuxtLink to="/students" class="text-gray-700 hover:text-blue-600">
          Students
        </NuxtLink>

        <NuxtLink to="/destinations" class="text-gray-700 hover:text-blue-600">
          Study Destinations
          <ChevronDownIcon class="w-4 h-4 inline-block mb-1" />
        </NuxtLink>

        <NuxtLink to="/partners" class="text-gray-700 hover:text-blue-600">
          Partners
          <ChevronDownIcon class="w-4 h-4 inline-block mb-1" />
        </NuxtLink>

        <div class="flex items-center gap-2">
          <NuxtLink to="/register">
            <button class="bg-white text-[#E72700] px-6 py-2 rounded hover:bg-[#d61f00] hover:text-white border-blue-400 border-[1px]">
              Register
            </button>
          </NuxtLink>
          <NuxtLink to="/Login">
            <button class="bg-[#E72700] text-white px-6 py-2 rounded hover:bg-[#d61f00] border-blue-400 border-[1px]">
              Log In
            </button>
          </NuxtLink>
        </div>
      </div>

      <!-- User Icon (mobile only) -->
      <div>
        <UserIcon
          class="w-7 h-7 text-gray-700 hover:text-blue-600 cursor-pointer ml-[200px] lg:hidden"
        />
      </div>
    </div>

    <!-- Mobile Menu -->
    <div
      v-if="menuOpen"
      class="lg:hidden bg-white shadow-md absolute w-full left-0 top-[50px] px-4 py-3 space-y-3"
    >
      <NuxtLink to="/" class="block text-gray-700 hover:text-blue-600" @click="closeMenu">
        Home
      </NuxtLink>
      <NuxtLink to="/about" class="block text-gray-700 hover:text-blue-600" @click="closeMenu">
        About
      </NuxtLink>
      <NuxtLink to="/services" class="block text-gray-700 hover:text-blue-600" @click="closeMenu">
        Services
      </NuxtLink>
      <NuxtLink to="/contact" class="block text-gray-700 hover:text-blue-600" @click="closeMenu">
        Contact
      </NuxtLink>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount, watch } from 'vue'
import { useRoute } from 'vue-router'
import { Bars3Icon, XMarkIcon, UserIcon, ChevronDownIcon } from '@heroicons/vue/24/outline'

const menuOpen = ref(false)
const route = useRoute()

function closeMenu() {
  menuOpen.value = false
}

// Close mobile menu on scroll (only while open)
function handleScroll() {
  menuOpen.value = false
}

watch(menuOpen, (open) => {
  if (open) window.addEventListener('scroll', handleScroll, { passive: true })
  else window.removeEventListener('scroll', handleScroll)
})

// Close menu if resized to desktop (lg >= 1024px)
function handleResize() {
  if (window.innerWidth >= 1024) menuOpen.value = false
}

onMounted(() => {
  window.addEventListener('resize', handleResize)
})

// Optional: also close on route change
watch(() => route.fullPath, () => {
  menuOpen.value = false
})

onBeforeUnmount(() => {
  window.removeEventListener('resize', handleResize)
  window.removeEventListener('scroll', handleScroll)
})
</script>
