<script setup lang="ts">
definePageMeta({
    layout: 'default'
})

const features = [
    {
        title: 'Modern Design',
        description: 'Beautiful and responsive design built with Tailwind CSS',
        icon: '🎨'
    },
    {
        title: 'Fast Performance',
        description: 'Optimized for speed and efficiency',
        icon: '⚡'
    },
    {
        title: 'Easy to Use',
        description: 'Simple and intuitive user experience',
        icon: '🚀'
    }
]
</script>

<template>
    <main class="min-h-screen">
        <!-- Hero Section -->
        <section class="relative bg-gradient-primary text-white py-20">
            <div class="container mx-auto px-4 text-center">
                <h1 class="text-5xl md:text-6xl font-bold mb-6 animate-fade-in">
                    Welcome to <span class="text-white">SGE-HSEDU</span>
                </h1>
                <p class="text-xl md:text-2xl mb-8 max-w-3xl mx-auto opacity-90 animate-slide-up text-black-300">
                    A modern Nuxt.js application built with Tailwind CSS for the best development experience
                </p>
                <div class="flex flex-col sm:flex-row gap-4 justify-center">
                    <NuxtLink to="/signup">
                        <button class="btn-primary px-8 py-3 text-lg">
                            Get Started
                        </button>
                    </NuxtLink>
                    <NuxtLink to="/about">
                        <button class="btn-outline px-8 py-3 text-lg">
                            Learn More
                        </button>
                    </NuxtLink>
                </div>
            </div>
        </section>

        <!-- Features Section -->
        <section class="py-20 bg-black-900">
            <div class="container mx-auto px-4">
                <div class="text-center mb-16">
                    <h2 class="text-4xl font-bold text-white mb-4">Why Choose Us?</h2>
                    <p class="text-xl text-black-300 max-w-2xl mx-auto">
                        Discover the amazing features that make our platform stand out from the rest
                    </p>
                </div>

                <div class="grid md:grid-cols-3 gap-8">
                    <div v-for="feature in features" :key="feature.title"
                        class="card text-center hover:shadow-glow transition-all duration-300 hover:-translate-y-2">
                        <div class="text-6xl mb-4">{{ feature.icon }}</div>
                        <h3 class="text-2xl font-semibold text-white mb-3">{{ feature.title }}</h3>
                        <p class="text-black-300">{{ feature.description }}</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- CTA Section -->
        <section class="py-20 bg-black-950 text-white">
            <div class="container mx-auto px-4 text-center">
                <h2 class="text-4xl font-bold mb-6">Ready to Get Started?</h2>
                <p class="text-xl text-black-300 mb-8 max-w-2xl mx-auto">
                    Join thousands of developers who are already building amazing applications with our platform
                </p>
                <button class="btn-primary px-10 py-4 text-lg">
                    Start Building Today
                </button>
            </div>
        </section>
    </main>
</template>

<style scoped>
.container {
    max-width: 1200px;
}
</style>
