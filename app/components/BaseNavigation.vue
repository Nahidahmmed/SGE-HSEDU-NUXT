<script setup lang="ts">
const route = useRoute();
const isMenuOpen = ref(false);

const navigationItems = [
  { name: 'Home', href: '/', current: false },
  { name: 'About', href: '/about', current: false },
  { name: 'Services', href: '/services', current: false },
  { name: 'Contact', href: '/contact', current: false },
];

// Update current page based on route
const currentNavigationItems = computed(() => {
  return navigationItems.map(item => ({
    ...item,
    current: item.href === route.path
  }));
});

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>

<template>
  <nav class="bg-black-950 border-b border-black-800">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between h-16">
        <!-- Logo -->
        <div class="flex items-center">
          <div class="flex-shrink-0">
            <h1 class="text-2xl font-bold text-gradient">SGE-HSEDU</h1>
          </div>
        </div>

        <!-- Desktop Navigation -->
        <div class="hidden md:flex items-center space-x-8">
          <NuxtLink v-for="item in currentNavigationItems" :key="item.name" :to="item.href" :class="[
            'nav-link',
            item.current ? 'nav-link-active' : ''
          ]">
            {{ item.name }}
          </NuxtLink>

          <NuxtLink to="/signup">
            <button class="btn-primary">
              Get Started
            </button>
          </NuxtLink>
        </div>

        <!-- Mobile menu button -->
        <div class="md:hidden flex items-center">
          <button @click="toggleMenu" class="text-white hover:text-black-300 focus:outline-none focus:text-black-300">
            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path v-if="!isMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                d="M4 6h16M4 12h16M4 18h16" />
              <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>
      </div>
    </div>

    <!-- Mobile Navigation -->
    <div v-show="isMenuOpen" class="md:hidden border-t border-black-800 bg-black-900">
      <div class="px-2 pt-2 pb-3 space-y-1">
        <NuxtLink v-for="item in currentNavigationItems" :key="item.name" :to="item.href" :class="[
          'block nav-link',
          item.current ? 'nav-link-active' : ''
        ]" @click="isMenuOpen = false">
          {{ item.name }}
        </NuxtLink>

        <div class="pt-4">
          <NuxtLink to="/signup">
            <button class="w-full btn-primary">
              Get Started
            </button>
          </NuxtLink>
        </div>
      </div>
    </div>
  </nav>
</template>
